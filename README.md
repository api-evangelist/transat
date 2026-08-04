# Transat (transat)

<!-- API-EVANGELIST-PROVENANCE:BEGIN -->
> ### About this repository
>
> **This is not our API.** This repository is an independent, third-party profile of a company's
> **publicly available** API surface, maintained by [API Evangelist](https://apievangelist.com).
> API Evangelist does not operate, host, resell, or support this company's APIs, and is not
> affiliated with or endorsed by the company unless stated on the profile.
>
> **Where the information came from.** Everything here is assembled from material a member of the
> public can reach with a browser and no credentials — the company's own website, developer portal
> and documentation, the specifications it publishes for public use (OpenAPI, AsyncAPI, JSON Schema,
> `apis.json`, `llms.txt` and similar), its public repositories, and its public status, pricing and
> changelog pages. **Nothing here is obtained by breaching a system, defeating an access control, or
> using credentials of any kind.**
>
> **The rating is an independent assessment.** The Kin Score and Agent Readiness rating are
> independently calculated scores of a company's *public* API artifacts, produced by API Evangelist
> against a published rubric. They are not certifications, endorsements, security assessments, or
> audits, and they score published artifacts — not the quality, safety, or security of the software.
>
> **Corrections, re-scores, and removal are free.** No partnership, contract, or purchase is
> required, and you do not need to justify the request.
>
> - **Something wrong?** Open an issue on this repository, or email
>   [info@apievangelist.com](mailto:info@apievangelist.com).
> - **Published something new?** Ask for a re-score and we will re-run the rating.
> - **Want the listing taken down?** Say so and we will honor it. The profile is reduced to your
>   company name, a factual description, and a link to your own site, and the company is recorded as
>   **unrated** — never scored zero for having asked.
>
> **Response times.** Acknowledgement within **one business day**; removal or restriction within
> **two business days**; corrections and re-scores within **five business days**.
>
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

Transat A.T. Inc. (TSX: TRZ) is a Montreal-headquartered, vertically integrated Canadian leisure travel group. It operates Air Transat (IATA carrier code TS), a transatlantic and sun-destination leisure airline, alongside tour-operating brands (Transat / Transat Tours Canada Inc.) and one of Canada's largest retail travel agency networks (Transat Travel, Voyages Transat, Marlin Travel, Club Voyages). It sits on the supply side of the distribution chain: it owns the seat and package inventory, sells it direct through transat.com and airtransat.com, through its own retail agencies, through GDS/CRS EDIFACT channels governed by IATA Resolution 850m and BSP settlement, and — since its published NDC programme — through an Accelya Farelogix NDC gateway and a named set of NDC aggregators. Its API posture is partner-gated but not opaque: Air Transat publishes a public NDC connectivity page and a publicly downloadable 46-page "Air Transat API specifications" document, but that document is a proprietary Radixx ConnectPoint SOAP contract (v2.2.4, May 2023), not an IATA NDC schema. There is no self-serve developer portal, no machine-readable OpenAPI or WSDL, no published base URL, no sandbox, no bulk export operation, and no IATA NDC certification level is claimed.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/transat/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/transat/refs/heads/main/apis.yml)

## Tags

- Travel
- Canada
- Aviation
- Airline
- Distribution
- NDC
- Booking
- Tour Operator
- Corporate Travel
- GDS

## Timestamps

- **Created:** 2026-07-28
- **Modified:** 2026-07-28

## APIs

### Air Transat NDC Direct Connect API (Radixx ConnectPoint)

The direct-connect flight shopping, booking, payment and servicing API that Air Transat publishes to OTA and technology partners under its NDC programme. The only technical contract Transat publishes for it is the "Air Transat API specifications" PDF — the Radixx ConnectPoint API, Flight Booking Detailed View, version 2.2.4, updated May 2023 — a SOAP 1.1 / .NET WCF service. Authentication is a LogonID / Password exchange returning a SecurityGUID, scoped to `AccessibleCarrierCode` `TS`. No base URL, WSDL, sandbox or OpenAPI is published.

- **Human URL:** [https://www.airtransat.com/en-CA/air-transat-ndc](https://www.airtransat.com/en-CA/air-transat-ndc)
- **Base URL:** not published

#### Documented operations

| Stage | Operations |
| --- | --- |
| Shopping | `RetrieveFastFareSearch`, `RetrieveFareQuoteShop` |
| Offers and pricing | `RetrieveFareQuote`, `ConvertCurrencies` |
| Session and identity | `RetrieveSecurityToken`, `LoginTravelAgent`, `RetrieveAgencyCommission` |
| Booking and order | `SummaryPNR`, `CreatePNR` (CommitSummary), `CreatePNR` (SaveReservation), `RetrievePNR` |
| Payment | `ProcessPNRPayment` |
| Events | `Notification` |

#### Tags

- NDC
- Distribution
- Shopping
- Booking
- Order Management
- Payment
- Ticketing
- SOAP

#### Properties

- [Documentation](https://www.airtransat.com/en-CA/air-transat-ndc)
- [API Reference](https://staticcontent.transat.com/airtransat/pdf/EN/NDC-TS-Radixx-ConnectPoint-API-book-Flight.pdf) — Air Transat API specifications, Radixx ConnectPoint API v2.2.4 (PDF, 46 pages)
- [Documentation (French)](https://www.airtransat.com/fr-CA/air-transat-ndc)
- [Documentation](https://w3.accelya.com/) — Accelya Farelogix, Air Transat's named NDC technology partner
- [Terms of Service](https://www.airtransat.com/en-CA/legal-notice/crs-booking-and-ticketing-policy) — CRS Booking and Ticketing Procedures Policy

## Switching cost

The full evidence trail lives in [review.yml](review.yml). In short:

- **Interface shape:** `standard-plus-proprietary`. IATA NDC is asserted on the connectivity page; the only downloadable contract is proprietary Radixx ConnectPoint SOAP.
- **Second source:** `alternatives-with-migration`. The content is single-origin, but Transat publishes six aggregator routes to it — Travelfusion, Clarity TTS, Farenexus, Onefly, and (soon) Mystifly and Duffel — plus the Sprk and Transat Agent Direct portals and the legacy GDS.
- **Exit path:** `export-on-request`. No bulk export operation; `RetrievePNR` is one record at a time. Consumer portability is EEA-only, on request, with a possible administrative fee.
- **Identifier portability:** IATA carrier code TS, IATA airport codes, IATA agency numbers, PNR record locators, 649 traffic documents and BSP references travel; Radixx `SecurityGUID`, `FareID`, `TripID` and Transat-assigned agency credentials do not.
- **Contractual lock-in:** the CRS policy bars sharing or redistributing Air Transat content to any third-party agent, GDS or metasearch engine without prior written consent, requires booking and ticketing within the same CRS, and enforces via Agency Debit Memos under IATA Resolution 850m.
- **Access gate:** `commercial-agreement`. Contact `commercial.ndc@transat.com`; Transat configures a pre-defined travel agency and issues the IATA number and credentials.
- **Distribution model:** `ndc-direct`, with the legacy EDIFACT/GDS channel explicitly surcharged relative to NDC.

## Common

- [Website](https://www.transat.com/)
- [Air Transat](https://www.airtransat.com/)
- [Air Transat NDC connectivity page](https://www.airtransat.com/en-CA/air-transat-ndc)
- [Transat Agent Direct](https://www.transatagentdirect.com/) — travel professional portal (login required)
- [Terms of Use of the Air Transat Sites](https://www.airtransat.com/en-CA/legal-notice/terms-of-use-of-the-air-transat-sites)
- [Transat website terms and conditions](https://www.transat.com/en-CA/website-terms-and-conditions)
- [Privacy Policy](https://www.airtransat.com/en-CA/legal-notice/privacy-policy)
- [Legal notice](https://www.airtransat.com/en-CA/legal-notice)
- [Conditions of carriage and tariffs](https://www.airtransat.com/en-CA/legal-notice/conditions-of-carriage-and-tariffs)
- [Experience Transat blog](https://experience.transat.com/)
- [LinkedIn](https://www.linkedin.com/company/air-transat)
- [GitHub organization](https://github.com/AirTransat)
- [Investors](https://www.transat.com/en-CA/corporate/investors)
- [About Transat](https://www.transat.com/en-CA/corporate/about-transat)

## Maintainers

- Kin Lane — kin@apievangelist.com

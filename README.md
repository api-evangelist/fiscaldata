# U.S. Treasury Fiscal Data (fiscaldata)

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
> **Not from the company, and here with a question?** You are welcome here — we would rather be the
> front line and point you the right way than have a good report go nowhere. What this repository
> can answer is narrow, though, so it is worth knowing who you are actually looking for:
>
> - **A question about how the API works, an account, billing, or a bug in the service** — that is
>   the company's own support, not us. We profile this API; we do not operate it and cannot see
>   your account.
> - **A bug in an open-source project we only catalog** — file it on that project's own repository.
>   This has happened with a real and correct bug report that reached us instead of the people who
>   could fix it, which helped nobody.
> - **Anything about this listing itself** — the description, the tags, the rating, a missing or
>   wrong artifact — is ours. Open an issue here.
> - **Not sure, or something general about API Evangelist or APIs.io** — open an issue on the
>   [APIs.io Inbox](https://github.com/api-search/inbox) and we will route it.
>
> **This repository contains no software, and we will never ask you to download anything.** There is
> no build, release, installer, or binary here — only text and machine-readable API descriptions, so
> there is nothing here that can be "corrupt" or need "repairing". Any issue, comment, or email
> claiming otherwise and offering a download link is not from us and is hostile. Do not follow the
> link; it is a lure. Report it to GitHub and, if you like, tell us at
> [info@apievangelist.com](mailto:info@apievangelist.com) so we can take it down.
>
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

U.S. Treasury Fiscal Data is a free, public source for federal government financial data published by the U.S. Bureau of the Fiscal Service. Its REST API serves machine-readable **government reports** and **economic indicators** — the national debt, average interest rates on Treasury securities, daily and monthly Treasury statements of federal revenue and spending, Treasury reporting rates of exchange, and Treasury securities auctions — as JSON, CSV, or XML.

**Access model: completely free and open.** No registration, no API key, and no authentication are required. The underlying data is a U.S. Government work in the public domain. Each dataset endpoint responds from a single database table and supports field selection (`fields`), filtering (`filter`), sorting (`sort`), format selection (`format`), and pagination (`page[number]` / `page[size]`).

**Base URL:** `https://api.fiscaldata.treasury.gov/services/api/fiscal_service`

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/fiscaldata/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/fiscaldata/refs/heads/main/apis.yml)

## Tags

- Government Data
- Treasury
- Economic Indicators
- Interest Rates
- Open Data
- National Debt
- Government Reports
- Public Domain
- Federal Finance

## Timestamps

- **Created:** 2026-07-11
- **Modified:** 2026-07-11

## Query Parameters (all endpoints)

- `fields` — comma-separated columns to return, e.g. `record_date,tot_pub_debt_out_amt`
- `filter` — `field:operator:value` (operators: `lt`, `lte`, `gt`, `gte`, `eq`, `in`), comma-separated for AND
- `sort` — comma-separated fields; prefix `-` for descending, e.g. `-record_date`
- `format` — `json` (default), `csv`, or `xml`
- `page[number]` — page number (1-based)
- `page[size]` — records per page (max 10000)

## APIs

### Treasury Debt API

National debt figures as machine-readable government reports. Debt to the Penny reports total public debt outstanding each day (debt held by the public plus intragovernmental holdings); the Interest Expense on the Debt dataset reports monthly and fiscal-year-to-date interest paid on the debt.

- **Human URL:** [https://fiscaldata.treasury.gov/datasets/debt-to-the-penny/debt-to-the-penny](https://fiscaldata.treasury.gov/datasets/debt-to-the-penny/debt-to-the-penny)
- **Base URL:** `https://api.fiscaldata.treasury.gov/services/api/fiscal_service`
- Example: `GET /v2/accounting/od/debt_to_penny?fields=record_date,tot_pub_debt_out_amt&sort=-record_date`

### Average Interest Rates API

Monthly average interest rates on U.S. Treasury securities by security type and description — Bills, Notes, Bonds, TIPS, Floating Rate Notes, and government account series. A core economic indicator for the government's cost of borrowing.

- **Human URL:** [https://fiscaldata.treasury.gov/datasets/average-interest-rates-treasury-securities/average-interest-rates-on-u-s-treasury-securities](https://fiscaldata.treasury.gov/datasets/average-interest-rates-treasury-securities/average-interest-rates-on-u-s-treasury-securities)
- **Base URL:** `https://api.fiscaldata.treasury.gov/services/api/fiscal_service`
- Example: `GET /v2/accounting/od/avg_interest_rates?filter=record_date:gte:2024-01-01&sort=-record_date`

### Daily Treasury Statement API

The Daily Treasury Statement (DTS) summarizes the federal government's cash and debt operations each business day — the Treasury General Account operating cash balance, deposits and withdrawals of operating cash, and public debt transactions.

- **Human URL:** [https://fiscaldata.treasury.gov/datasets/daily-treasury-statement/operating-cash-balance](https://fiscaldata.treasury.gov/datasets/daily-treasury-statement/operating-cash-balance)
- **Base URL:** `https://api.fiscaldata.treasury.gov/services/api/fiscal_service`
- Example: `GET /v1/accounting/dts/operating_cash_balance?fields=record_date,account_type,open_today_bal&sort=-record_date`

### Monthly Treasury Statement API

The Monthly Treasury Statement (MTS) is the official monthly report of federal receipts (revenue), outlays (spending), and the resulting budget surplus or deficit — the primary economic indicators for U.S. fiscal policy.

- **Human URL:** [https://fiscaldata.treasury.gov/datasets/monthly-treasury-statement/summary-of-receipts-and-outlays-of-the-u-s-government](https://fiscaldata.treasury.gov/datasets/monthly-treasury-statement/summary-of-receipts-and-outlays-of-the-u-s-government)
- **Base URL:** `https://api.fiscaldata.treasury.gov/services/api/fiscal_service`
- Example: `GET /v1/accounting/mts/mts_table_4?sort=-record_date`

### Treasury Reporting Rates of Exchange API

The official U.S. Treasury exchange rates used to convert foreign currency balances into U.S. dollars for reporting, provided quarterly per country and currency.

- **Human URL:** [https://fiscaldata.treasury.gov/datasets/treasury-reporting-rates-exchange/treasury-reporting-rates-of-exchange](https://fiscaldata.treasury.gov/datasets/treasury-reporting-rates-exchange/treasury-reporting-rates-of-exchange)
- **Base URL:** `https://api.fiscaldata.treasury.gov/services/api/fiscal_service`
- Example: `GET /v1/accounting/od/rates_of_exchange?filter=record_date:gte:2024-01-01&sort=-record_date`

### Treasury Securities API

Treasury securities auction data — CUSIP, security type and term, auction/issue/maturity dates, price per 100, yields, and bid metrics for Bills, Notes, Bonds, TIPS, and FRNs.

- **Human URL:** [https://fiscaldata.treasury.gov/datasets/auctions-query/auctions-query](https://fiscaldata.treasury.gov/datasets/auctions-query/auctions-query)
- **Base URL:** `https://api.fiscaldata.treasury.gov/services/api/fiscal_service`
- Example: `GET /v1/accounting/od/auctions_query?sort=-auction_date`

## Common Properties

- [Website](https://fiscaldata.treasury.gov)
- [Documentation](https://fiscaldata.treasury.gov/api-documentation/)
- [Support — Fiscal Service Enterprise API Community](https://api-community.fiscal.treasury.gov/)
- [GitHub — fiscal-data source](https://github.com/fedspendingtransparency/fiscal-data)
- [Plans](plans/fiscaldata-plans-pricing.yml)
- [Rate Limits](rate-limits/fiscaldata-rate-limits.yml)
- [Fin Ops](finops/fiscaldata-finops.yml)

## Access and Licensing

- **Authentication:** None. The API is open and requires no key or account.
- **Cost:** Free. There is no paid tier and no billing.
- **License:** U.S. Government work in the public domain; data may be used, reproduced, and redistributed freely.
- **Availability:** Subject to federal government operations; no SLA is offered.

## Maintainers

**FN:** Kin Lane
**Email:** kin@apievangelist.com

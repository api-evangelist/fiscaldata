# U.S. Treasury Fiscal Data (fiscaldata)

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

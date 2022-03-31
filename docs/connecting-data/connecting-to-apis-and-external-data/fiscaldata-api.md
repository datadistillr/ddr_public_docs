---
description: How to Connect DataDistillr to the Fiscal Data API
---

## Connecting to Fiscal Data
No account is necessary for this API. Here is the website [https://fiscaldata.treasury.gov/][link-0]{target="_blank"}

???+ cost

    This API is free.


???+ rlimit "Rate limits"

    The API does not have any information about rate limits.


## How to Connect DataDistillr to Fiscal Data
To set up a data source connect for Fiscal Data, you will need to have:

- A [unique name](#name) for your data source connection to be used in queries

### Data Source Form
To locate the Fiscal Data form, follow the steps in [Connecting Your Data to DataDistillr](../../). When you get to the window to choose the data source type, select API as shown below.


<figure markdown>
  ![Data Source Wizard][image-0]{ width="100%" }
</figure>



On the API screen, select Fiscal Data from the list of API forms.

<figure markdown>
  ![List of APIs][image-1]{ width="100%" }
</figure>



The following form will appear. Instructions can be found below on how to find the information required to fill each on the Fiscal Data API form.

Once you have filled out all the fields, press the green 'Save' button, and your API will be connected!

<figure markdown>
  ![Fiscal Data Form][image-3]{ width="100%" }
</figure>

### Name
Enter any name that will help you recognize this data source within your query window.

!!! info "Acceptable Characters Include"

    - lowercase alphanumeric characters
    - underscores


## Endpoints
The table below shows a list of endpoints available to connect within the DataDistillr application. If you need to connect to any endpoints not listed in the table below, please use the [Custom API](custom-apis.md) Form.

There are a total of 80 endpoints. Many datasets are associated with only one data table, and thus, one API endpoint. There are some datasets comprised of more than one data table, and therefore have more than one endpoint.

Note that every API URL begins with the base URL:

``` 
https://api.fiscaldata.treasury.gov/services/api/fiscal_service
```

Thus, the full API request URL would be the Base URL + Endpoint. 

!!! example "Full API request example"

    ``` 
    https://api.fiscaldata.treasury.gov/services/api/fiscal_service/v2/accounting/od/avg_interest_rates
    ```

### Parameters
Parameters can be included in an API request by modifying the URL. This will specify the criteria to determine which records will be returned, as well as the ordering and format of the data returned. More information about each parameter can be found below.

Available parameters include (every endpoint has these as optional parameters):

- Fields
- Filters
- Sorting
- Format
- Pagination
    - page[size]
    - page[number]



The table below lists the available endpoints by dataset and data table.

| Endpoint                                              | Table Name                                                                      | Dataset                                                                                                |
|-------------------------------------------------------|---------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------|
| `/v2/debt/tror/data_act_compliance`                   | 120 Day Delinquent Debt Referral Compliance Report                              | [120 Day Delinquent Debt Referral Compliance Report][link-1]{target="_blank"}                          |
| `/v2/accounting/od/redemption_tables`                 | Redemption Tables                                                               | [Accrual Savings Bonds Redemption Tables][link-2]{target="_blank"}                                     |
| `/v2/accounting/od/title_xii`                         | Advances to State Unemployment Funds (Social Security Act Title XII)            | [Advances to State Unemployment Funds (Social Security Act Title XII)][link-3]{target="_blank"}        |
| `/v2/accounting/od/avg_interest_rates`                | Average Interest Rates on U.S. Treasury Securities                              | [Average Interest Rates on U.S. Treasury Securities][link-4]{target="_blank"}                          |
| `/v1/accounting/dts/dts_table_1`                      | Operating Cash Balance                                                          | [Daily Treasury Statement (DTS)][link-5]{target="_blank"}                                              |
| `/v1/accounting/dts/dts_table_2`                      | Deposits and Withdrawals of Operating Cash                                      | [Daily Treasury Statement (DTS)][link-5]{target="_blank"}                                              |
| `/v1/accounting/dts/dts_table_3a`                     | Public Debt Transactions                                                        | [Daily Treasury Statement (DTS)][link-5]{target="_blank"}                                              |
| `/v1/accounting/dts/dts_table_3b`                     | Adjustment of Public Debt Transactions to Cash Basis                            | [Daily Treasury Statement (DTS)][link-5]{target="_blank"}                                              |
| `/v1/accounting/dts/dts_table_3c`                     | Debt Subject to Limit                                                           | [Daily Treasury Statement (DTS)][link-5]{target="_blank"}                                              |
| `/v1/accounting/dts/dts_table_4`                      | Federal Tax Deposits                                                            | [Daily Treasury Statement (DTS)][link-5]{target="_blank"}                                              |
| `/v1/accounting/dts/dts_table_5`                      | Short-Term Cash Investments                                                     | [Daily Treasury Statement (DTS)][link-5]{target="_blank"}                                              |
| `/v1/accounting/dts/dts_table_6`                      | Income Tax Refunds Issued                                                       | [Daily Treasury Statement (DTS)][link-5]{target="_blank"}                                              |
| `/v2/accounting/od/debt_to_penny`                     | Debt to the Penny                                                               | [Debt to the Penny][link-6]{target="_blank"}                                                           |
| `/v2/accounting/od/interest_uninvested`               | Federal Borrowings Program: Interest on Uninvested Funds                        | [Federal Borrowings Program: Interest on Uninvested Funds][link-7]{target="_blank"}                    |
| `/v2/accounting/od/interest_cost_fund`                | Federal Investments Program: Interest Cost by Fund                              | [Federal Investments Program: Interest Cost by Fund][link-8]{target="_blank"}                          |
| `/v2/accounting/od/statement_net_cost`                | Statements of Net Cost                                                          | [Financial Report of the U.S. Government][link-9]{target="_blank"}                                     |
| `/v1/accounting/od/net_position`                      | Statements of Operations and Changes in Net Position                            | [Financial Report of the U.S. Government][link-9]{target="_blank"}                                     |
| `/v1/accounting/od/reconciliations`                   | Reconciliations of Net Operating Cost and Budget Deficit                        | [Financial Report of the U.S. Government][link-9]{target="_blank"}                                     |
| `/v1/accounting/od/cash_balance`                      | Statements of Changes in Cash Balance from Budget and Other Activities          | [Financial Report of the U.S. Government][link-9]{target="_blank"}                                     |
| `/v2/accounting/od/balance_sheets`                    | Balance Sheets                                                                  | [Financial Report of the U.S. Government][link-9]{target="_blank"}                                     |
| `/v1/accounting/od/long_term_projections`             | Statements of Long-Term Fiscal Projections                                      | [Financial Report of the U.S. Government][link-9]{target="_blank"}                                     |
| `/v1/accounting/od/social_insurance`                  | Statements of Social Insurance                                                  | [Financial Report of the U.S. Government][link-9]{target="_blank"}                                     |
| `/v1/accounting/od/insurance_amounts`                 | Statements of Changes in Social Insurance Amounts                               | [Financial Report of the U.S. Government][link-9]{target="_blank"}                                     |
| `/v2/accounting/od/gift_contributions`                | Gift Contributions to Reduce the Public Debt                                    | [Gift Contributions to Reduce the Public Debt][link-10]{target="_blank"}                               |
| `/v2/accounting/od/debt_outstanding`                  | Historical Debt Outstanding                                                     | [Historical Debt Outstanding][link-11]{target="_blank"}                                                |
| `/v2/accounting/od/qualified_tax`                     | Historical Qualified Tax Credit Bond Interest Rates                             | [Historical Qualified Tax Credit Bond Interest Rates][link-12]{target="_blank"}                        |
| `/v2/accounting/od/interest_expense`                  | Interest Expense on the Public Debt Outstanding                                 | [Interest Expense on the Public Debt Outstanding][link-13]{target="_blank"}                            |
| `/v2/payments/jfics/jfics_congress_report`            | Judgment Fund: Annual Report to Congress                                        | [Judgment Fund: Annual Report to Congress][link-14]{target="_blank"}                                   |
| `/v2/accounting/od/slgs_statistics`                   | Monthly State and Local Government Series (SLGS) Securities Program             | [Monthly State and Local Government Series (SLGS) Securities Program][link-15]{target="_blank"}        |
| `/v1/accounting/mts/mts_table_1`                      | Summary of Receipts, Outlays, and the Deficit/Surplus of the U.S. Government    | [Monthly Treasury Statement (MTS)][link-16]{target="_blank"}                                           |
| `/v1/accounting/mts/mts_table_2`                      | Summary of Budget and Off-Budget Results and Financing of the U.S. Government   | [Monthly Treasury Statement (MTS)][link-16]{target="_blank"}                                           |
| `/v1/accounting/mts/mts_table_3`                      | Summary of Receipts and Outlays of the U.S. Government                          | [Monthly Treasury Statement (MTS)][link-16]{target="_blank"}                                           |
| `/v1/accounting/mts/mts_table_4`                      | Receipts of the U.S. Government                                                 | [Monthly Treasury Statement (MTS)][link-16]{target="_blank"}                                           |
| `/v1/accounting/mts/mts_table_5`                      | Outlays of the U.S. Government                                                  | [Monthly Treasury Statement (MTS)][link-16]{target="_blank"}                                           |
| `/v1/accounting/mts/mts_table_6`                      | Means of Financing the Deficit or Disposition of Surplus by the U.S. Government | [Monthly Treasury Statement (MTS)][link-16]{target="_blank"}                                           |
| `/v1/accounting/mts/mts_table_6a`                     | Analysis of Change in Excess of Liabilities of the U.S. Government              | [Monthly Treasury Statement (MTS)][link-16]{target="_blank"}                                           |
| `/v1/accounting/mts/mts_table_6b`                     | Securities Issued by Federal Agencies Under Special Financing Authorities       | [Monthly Treasury Statement (MTS)][link-16]{target="_blank"}                                           |
| `/v1/accounting/mts/mts_table_6c`                     | Federal Agency Borrowing Financed Through the Issue of Treasury Securities      | [Monthly Treasury Statement (MTS)][link-16]{target="_blank"}                                           |
| `/v1/accounting/mts/mts_table_6d`                     | Investments of Federal Government Accounts in Federal Securities                | [Monthly Treasury Statement (MTS)][link-16]{target="_blank"}                                           |
| `/v1/accounting/mts/mts_table_6e`                     | Guaranteed and Direct Loan Financing, Net Activity                              | [Monthly Treasury Statement (MTS)][link-16]{target="_blank"}                                           |
| `/v1/accounting/mts/mts_table_7`                      | Receipts and Outlays of the U.S. Government by Month                            | [Monthly Treasury Statement (MTS)][link-16]{target="_blank"}                                           |
| `/v1/accounting/mts/mts_table_8`                      | Trust Fund Impact on Budget Results and Investment Holdings                     | [Monthly Treasury Statement (MTS)][link-16]{target="_blank"}                                           |
| `/v1/accounting/mts/mts_table_9`                      | Summary of Receipts by Source, and Outlays by Function of the U.S. Government   | [Monthly Treasury Statement (MTS)][link-16]{target="_blank"}                                           |
| `/v2/accounting/od/record_setting_auction`            | Record-Setting Auction                                                          | [Record-Setting Treasury Securities Auction Data][link-17]{target="_blank"}                            |
| `/v1/accounting/od/slgs_savings_bonds`                | Savings Bonds Securities                                                        | [Savings Bonds Securities Sold][link-18]{target="_blank"}                                              |
| `/v2/accounting/od/sb_value`                          | Savings Bonds Value Files                                                       | [Savings Bonds Value Files][link-19]{target="_blank"}                                                  |
| `/v1/accounting/od/schedules_fed_debt`                | Schedules of Federal Debt by Month                                              | [Schedules of Federal Debt][link-20]{target="_blank"}                                                  |
| `/v1/accounting/od/schedules_fed_debt_fytd`           | Schedules of Federal Debt, Fiscal Year-to-Date                                  | [Schedules of Federal Debt][link-20]{target="_blank"}                                                  |
| `/v1/accounting/od/schedules_fed_debt_daily_activity` | Daily Activity                                                                  | [Schedules of Federal Debt by Day][link-21]{target="_blank"}                                           |
| `/v1/accounting/od/schedules_fed_debt_daily_summary`  | Daily Summary                                                                   | [Schedules of Federal Debt by Day][link-21]{target="_blank"}                                           |
| `/v1/accounting/od/securities_sales`                  | Sales                                                                           | [Securities Issued In TreasuryDirect][link-22]{target="_blank"}                                        |
| `/v1/accounting/od/securities_sales_term`             | Sales by Term                                                                   | [Securities Issued In TreasuryDirect][link-22]{target="_blank"}                                        |
| `/v1/accounting/od/securities_transfers`              | Transfers of Marketable Securities                                              | [Securities Issued In TreasuryDirect][link-22]{target="_blank"}                                        |
| `/v1/accounting/od/securities_conversions`            | Conversions of Paper Savings Bonds                                              | [Securities Issued In TreasuryDirect][link-22]{target="_blank"}                                        |
| `/v1/accounting/od/securities_redemptions`            | Redemptions                                                                     | [Securities Issued In TreasuryDirect][link-22]{target="_blank"}                                        |
| `/v1/accounting/od/securities_outstanding`            | Outstanding                                                                     | [Securities Issued In TreasuryDirect][link-22]{target="_blank"}                                        |
| `/v1/accounting/od/securities_c_of_i`                 | Certificates of Indebtedness                                                    | [Securities Issued In TreasuryDirect][link-22]{target="_blank"}                                        |
| `/v1/accounting/od/securities_accounts`               | Accounts                                                                        | [Securities Issued In TreasuryDirect][link-22]{target="_blank"}                                        |
| `/v1/accounting/od/slgs_securities`                   | State and Local Government Series Securities (Non-Marketable)                   | [State and Local Government Series Securities (Non-Marketable)][link-23]{target="_blank"}              |
| `/v1/debt/top/top_federal`                            | Federal Collections                                                             | [Treasury Offset Program][link-24]{target="_blank"}                                                    |
| `/v1/debt/top/top_state`                              | State Programs                                                                  | [Treasury Offset Program][link-24]{target="_blank"}                                                    |
| `/v2/debt/tror`                                       | Treasury Report on Receivables Full Data                                        | [Treasury Report on Receivables (TROR)][link-25]{target="_blank"}                                      |
| `/v2/debt/tror/collected_outstanding_recv`            | Collected and Outstanding Receivables                                           | [Treasury Report on Receivables (TROR)][link-25]{target="_blank"}                                      |
| `/v2/debt/tror/delinquent_debt`                       | Delinquent Debt                                                                 | [Treasury Report on Receivables (TROR)][link-25]{target="_blank"}                                      |
| `/v2/debt/tror/collections_delinquent_debt`           | Collections on Delinquent Debt                                                  | [Treasury Report on Receivables (TROR)][link-25]{target="_blank"}                                      |
| `/v2/debt/tror/written_off_delinquent_debt`           | Written Off Delinquent Debt                                                     | [Treasury Report on Receivables (TROR)][link-25]{target="_blank"}                                      |
| `/v1/accounting/od/rates_of_exchange`                 | Treasury Reporting Rates of Exchange                                            | [Treasury Reporting Rates of Exchange][link-26]{target="_blank"}                                       |
| `/v2/revenue/rcm`                                     | U.S. Government Revenue Collections                                             | [U.S. Government Revenue Collections][link-27]{target="_blank"}                                        |
| `/v1/debt/mspd/mspd_table_1`                          | Summary of Treasury Securities Outstanding                                      | [U.S. Treasury Monthly Statement of the Public Debt (MSPD)][link-28]{target="_blank"}                  |
| `/v1/debt/mspd/mspd_table_2`                          | Statutory Debt Limit                                                            | [U.S. Treasury Monthly Statement of the Public Debt (MSPD)][link-28]{target="_blank"}                  |
| `/v1/debt/mspd/mspd_table_3`                          | Detail of Treasury Securities Outstanding                                       | [U.S. Treasury Monthly Statement of the Public Debt (MSPD)][link-28]{target="_blank"}                  |
| `/v1/debt/mspd/mspd_table_3_market`                   | Detail of Marketable Treasury Securities Outstanding                            | [U.S. Treasury Monthly Statement of the Public Debt (MSPD)][link-28]{target="_blank"}                  |
| `/v1/debt/mspd/mspd_table_3_nonmarket`                | Detail of Non-Marketable Treasury Securities Outstanding                        | [U.S. Treasury Monthly Statement of the Public Debt (MSPD)][link-28]{target="_blank"}                  |
| `/v1/debt/mspd/mspd_table_4`                          | Historical Data                                                                 | [U.S. Treasury Monthly Statement of the Public Debt (MSPD)][link-28]{target="_blank"}                  |
| `/v1/debt/mspd/mspd_table_5`                          | Holdings of Treasury Securities in Stripped Form                                | [U.S. Treasury Monthly Statement of the Public Debt (MSPD)][link-28]{target="_blank"}                  |
| `/v1/accounting/od/savings_bonds_report`              | Paper Savings Bonds Issues, Redemptions, and Maturities by Series               | [U.S. Treasury Savings Bonds: Issues, Redemptions, and Maturities by Series][link-29]{target="_blank"} |
| `/v1/accounting/od/savings_bonds_mud`                 | Matured Unredeemed Debt                                                         | [U.S. Treasury Savings Bonds: Issues, Redemptions, and Maturities by Series][link-29]{target="_blank"} |
| `/v1/accounting/od/savings_bonds_pcs`                 | Piece Information by Series                                                     | [U.S. Treasury Savings Bonds: Issues, Redemptions, and Maturities by Series][link-29]{target="_blank"} |
| `/v2/accounting/od/gold_reserve`                      | U.S. Treasury-Owned Gold                                                        | [U.S. Treasury-Owned Gold][link-30]{target="_blank"}                                                   |
| `/v2/accounting/od/utf_qtr_yields`                    | Unemployment Trust Fund: Quarterly Yields                                       | [Unemployment Trust Fund: Quarterly Yields][link-31]{target="_blank"}                                  |


### Nav Tree
The endpoints above will display as follows in the nav tree once your API has successfully connected. Note: the endpoints displayed in the previous picture are only the first nine endpoints.

<figure markdown>
  ![Fiscal Data Endpoints][image-5]{ width="100%" }
</figure>

## Sample Queries
The following queries are intended to help you get started, and make life simpler querying within your API. These are just 3 out of the 80 endpoints available.

For the following examples, suppose that my Fiscal Data API data source was called `myfiscaldataapi` and I want to query an endpoint. In the `FROM` clause, the endpoint goes after the Fiscal Data data source name:

!!! example "FROM Clause"

    ```sql
    FROM `myfiscaldataapi`.`<ENDPOINT>`
    ```

### Treasury Reporting Rates of Exchange
From the Treasury Reporting Rates of Exchange dataset, we are we have selected the following options:

- only return specific fields (country_currency_desc, exchange_rate, record_date), 
- only return data on the Canadian Dollar and Mexican Peso, and 
- only return data that falls between January 1, 2020, and the present.

```sql
SELECT * 
FROM `myfiscaldataapi`.`Treasury Reporting Rates of Exchange`
WHERE `fields`='country_currency_desc, exchange_rate, record_date' 
AND `filter`='country_currency_desc:in:(Canada-Dollar,Mexico-Peso),record_date:gte:2020-01-01'
LIMIT 100
```

### Debt to Penny
In this example we are performing nested sorting, first by year then by month on the Debt to Penny dataset.

```sql
SELECT * 
FROM `myfiscaldataapi`.`Debt to the Penny` 
WHERE `fields`='record_calendar_year,record_calendar_month'
AND `sort`='-record_calendar_year,-record_calendar_month'
LIMIT 1000
```

### State Programs
From the Treasury Offset Program dataset, return data with 50 records per page, and return the 10th page of data.

```sql
SELECT * 
FROM `myfiscaldataapi`.`Treasury Offset Program`
WHERE `page[number]`='10'
AND `page[size]`='50'
LIMIT 1000
```

[image-0]: ../../img/api/data-source-wizard-api-light.png "Data Source Wizard"
[image-1]: ../../img/api/fiscaldata/choose-form-fiscaldata-light.png "API Data Source selection"
[image-2]: ../../img/api/fiscaldata/choose-form-fiscaldata-dark.png "API Data Source selection"
[image-3]: ../../img/api/fiscaldata/fiscaldata-form-light.png "Fiscal Data form"
[image-4]: ../../img/api/fiscaldata/fiscaldata-form-dark.png "Fiscal Data form"
[image-5]: ../../img/api/fiscaldata/fiscaldata-nav-tree-light.png "Fiscal Data endpoints in query page nav tree sidebar"
[image-6]: ../../img/api/fiscaldata/fiscaldata-nav-tree-dark.png "Fiscal Data endoitns in query page nav tree sidebar"

[link-0]: https://fiscaldata.treasury.gov/ "Fiscal Data home page" 
[link-1]: https://fiscaldata.treasury.gov/datasets/delinquent-debt-referral-compliance/120-day-delinquent-debt-referral-compliance-report "120 Day Delinquent Debt Referral Compliance Report" 
[link-2]: https://fiscaldata.treasury.gov/datasets/redemption-tables/redemption-tables "Accrual Savings Bonds Redemption Tables"
[link-3]: https://fiscaldata.treasury.gov/datasets/ssa-title-xii-advance-activities/advances-to-state-unemployment-funds-social-security-act-title-xii "Asvances to State Unemployment Funds"
[link-4]: https://fiscaldata.treasury.gov/datasets/average-interest-rates-treasury-securities/average-interest-rates-on-u-s-treasury-securities "Average Interest Rates on U.S. Treasury Securities"
[link-5]: https://fiscaldata.treasury.gov/datasets/daily-treasury-statement/operating-cash-balance "Daily Treasury Statement"
[link-6]: https://fiscaldata.treasury.gov/datasets/debt-to-the-penny/debt-to-the-penny "Debt to the Penny"
[link-7]: https://fiscaldata.treasury.gov/datasets/fbp-interest-on-uninvested-funds/federal-borrowings-program-interest-on-uninvested-funds "Federal Borrowings Program: Interest on Uninvested Funds"
[link-8]: https://fiscaldata.treasury.gov/datasets/fip-interest-cost-by-fund/federal-investments-program-interest-cost-by-fund "Federal Investments Program: Interest Cost by Fund"
[link-9]: https://fiscaldata.treasury.gov/datasets/u-s-government-financial-report/statements-of-net-cost "Financial Report of the U.S. Government"
[link-10]: https://fiscaldata.treasury.gov/datasets/gift-contributions-reduce-debt-held-by-public/gift-contributions-to-reduce-the-public-debt "Gift Contributions to Reduce the Public Debt"
[link-11]: https://fiscaldata.treasury.gov/datasets/historical-debt-outstanding/historical-debt-outstanding "Historical Debt Outstanding"
[link-12]: https://fiscaldata.treasury.gov/datasets/qtcb-historical-interest-rates/historical-qualified-tax-credit-bond-interest-rates "Historical Qualified Tax Credit Bond Interest Rates"
[link-13]: https://fiscaldata.treasury.gov/datasets/interest-expense-debt-outstanding/interest-expense-on-the-public-debt-outstanding "Interest Expense on the Public Debt Outstanding"
[link-14]: https://fiscaldata.treasury.gov/datasets/judgment-fund-report-to-congress/judgment-fund-annual-report-to-congress "Judgment Fund: Annual Report to Congress"
[link-15]: https://fiscaldata.treasury.gov/datasets/slgs-securities-program-stats/monthly-state-and-local-government-series-slgs-securities-program "Monthly State and Local Government Series Securities Program"
[link-16]: https://fiscaldata.treasury.gov/datasets/monthly-treasury-statement/summary-of-receipts-outlays-and-the-deficit-surplus-of-the-u-s-government "Monthly Treasury Statement"
[link-17]: https://fiscaldata.treasury.gov/datasets/record-setting-auction-data/record-setting-auction "Record-Setting Treasury Securities Auction Data"
[link-18]: https://fiscaldata.treasury.gov/datasets/savings-bonds-securities/savings-bonds-securities "Savings Bonds Securities Solds"
[link-19]: https://fiscaldata.treasury.gov/datasets/savings-bond-value-files/savings-bonds-value-files "Savings Bonds Value Files"
[link-20]: https://fiscaldata.treasury.gov/datasets/schedules-federal-debt/schedules-of-federal-debt-by-month "Schedules of Federal Debt"
[link-21]: https://fiscaldata.treasury.gov/datasets/schedules-federal-debt-daily/daily-activity "Schedules of Federal Deby by Day"
[link-22]: https://fiscaldata.treasury.gov/datasets/securities-issued-in-treasurydirect/sales "Securities Issued In Treasury Direct"
[link-23]: https://fiscaldata.treasury.gov/datasets/slgs-securities/state-and-local-government-series-securities-non-marketable "State and Local Government Series Securities (Non-Marketable)"
[link-24]: https://fiscaldata.treasury.gov/datasets/treasury-offset-program/federal-collections "Treasury Offset Program"
[link-25]: https://fiscaldata.treasury.gov/datasets/treasury-report-on-receivables/treasury-report-on-receivables-full-data "Treasury Report on Receivables (TROR)"
[link-26]: https://fiscaldata.treasury.gov/datasets/treasury-reporting-rates-exchange/treasury-reporting-rates-of-exchange "Treasury Reporting Rates of Exchange"
[link-27]: https://fiscaldata.treasury.gov/datasets/revenue-collections-management/u-s-government-revenue-collections "U.S. Government Revenue Collections"
[link-28]: https://fiscaldata.treasury.gov/datasets/monthly-statement-public-debt/summary-of-treasury-securities-outstanding "U.S. Treasury Monthly Statement of the Public Debt (MSPD)"
[link-29]: https://fiscaldata.treasury.gov/datasets/savings-bonds-issues-redemptions-maturities-by-series/paper-savings-bonds-issues-redemptions-and-maturities-by-series "U.S. Treasury Savings Bonds: Issues, Redemptions, and Maturities by Series"
[link-30]: https://fiscaldata.treasury.gov/datasets/status-report-government-gold-reserve/u-s-treasury-owned-gold "U.S. Treasury-Owned Gold"
[link-31]: https://fiscaldata.treasury.gov/datasets/unemployment-trust-fund-yields/unemployment-trust-fund-quarterly-yields "Unemployment Trust Fund: Quarterly Yields"
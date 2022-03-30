---
description: How to Connect DataDistillr to the Fiscal Data API
---

## Connecting to Fiscal Data
Set up an account with [Fiscal Data]().

### Costs


### Rate Limits


## How to Connect DataDistillr to Fiscal Data
To set up a data source connect for Fiscal Data, you will need to have:

- A [unique name](#name) for your data source connection to be used in queries

### Data Source Form
To locate the Fiscal Data form, follow the steps in [Connecting Your Data to DataDistillr](../../). When you get to the window to choose the data source type, select API as shown below.






On the API screen, select Fiscal Data from the list of API forms.





The following form will appear. Instructions can be found below on how to find the information required to fill each on the Fiscal Data API form.

Once you have filled out all the fields, press the green 'Save' button, and your API will be connected!




### Name
Enter any name that will help you recognize this data source within your query window.

!!! info "Acceptable Characters Include"

    - lowercase alphanumeric characters
    - underscores


### API Key
An API key is generated within your account page. The following steps will navigate you to its location. Once created, copy the key and enter it in the Fiscal Data form under 'API key'.


## Endpoints
The table below shows a list of endpoints available to connect within the DataDistillr application. If you need to connect to any endpoints not listed in the table below, please use the [Custom API](../../) Form.

| Endpoint | Required | Optional | Description |
|----------|----------|----------|-------------|
|          |          |          |             |

[120 Day Delinquent Debt Referral Compliance Report][link-1]{target="_blank"}

### Nav Tree
The endpoints above will display as follows in the nav tree once your API has successfully connected.



## Sample Queries
The following queries are intended to help you get started, and make like simpler querying within your API.

For the following examples, suppose that my Fiscal Data API data source was called `myapi` and I want to query an endpoint. In the `FROM` clause, the endpoint goes after the Fiscal Data data source name.

!!! example "FROM Clause"

    ```sql
    FROM `myapi`.`<ENDPOINT>`
    ```


### Endpoint 1

```sql
SELECT * 
FROM `table`
WHERE `column`='value'
```

[image-0]: ../../img/api/data-source-wizard-api-light.png
[image-1]: ../../img/api/fiscaldata/choose-form-fiscaldata-light.png
[image-2]: ../../img/api/fiscaldata/choose-form-fiscaldata-dark.png
[image-3]: ../../img/api/fiscaldata/fiscaldata-form-light.png
[image-4]: ../../img/api/fiscaldata/fiscaldata-form-dark.png
[image-5]: ../../img/api/fiscaldata/fiscaldata-nav-tree-light.png
[image-6]: ../../img/api/fiscaldata/fiscaldata-nav-tree-dark.png

[link-1]: https://fiscaldata.treasury.gov/datasets/delinquent-debt-referral-compliance/120-day-delinquent-debt-referral-compliance-report "120 Day Delinquent Debt Referral Compliance Report" 
[link-2]: https://fiscaldata.treasury.gov/datasets/redemption-tables/redemption-tables
[link-3]: https://fiscaldata.treasury.gov/datasets/ssa-title-xii-advance-activities/advances-to-state-unemployment-funds-social-security-act-title-xii
[link-4]: https://fiscaldata.treasury.gov/datasets/average-interest-rates-treasury-securities/average-interest-rates-on-u-s-treasury-securities
[link-5]: https://fiscaldata.treasury.gov/datasets/daily-treasury-statement/operating-cash-balance
[link-6]: https://fiscaldata.treasury.gov/datasets/debt-to-the-penny/debt-to-the-penny
[link-7]: https://fiscaldata.treasury.gov/datasets/fbp-interest-on-uninvested-funds/federal-borrowings-program-interest-on-uninvested-funds
[link-8]: https://fiscaldata.treasury.gov/datasets/fip-interest-cost-by-fund/federal-investments-program-interest-cost-by-fund
[link-9]: https://fiscaldata.treasury.gov/datasets/u-s-government-financial-report/statements-of-net-cost
[link-10]: https://fiscaldata.treasury.gov/datasets/gift-contributions-reduce-debt-held-by-public/gift-contributions-to-reduce-the-public-debt
[link-11]: https://fiscaldata.treasury.gov/datasets/historical-debt-outstanding/historical-debt-outstanding
[link-12]: https://fiscaldata.treasury.gov/datasets/qtcb-historical-interest-rates/historical-qualified-tax-credit-bond-interest-rates
[link-13]: https://fiscaldata.treasury.gov/datasets/interest-expense-debt-outstanding/interest-expense-on-the-public-debt-outstanding
[link-14]: https://fiscaldata.treasury.gov/datasets/judgment-fund-report-to-congress/judgment-fund-annual-report-to-congress
[link-15]: https://fiscaldata.treasury.gov/datasets/slgs-securities-program-stats/monthly-state-and-local-government-series-slgs-securities-program
[link-16]: https://fiscaldata.treasury.gov/datasets/monthly-treasury-statement/summary-of-receipts-outlays-and-the-deficit-surplus-of-the-u-s-government
[link-17]: https://fiscaldata.treasury.gov/datasets/record-setting-auction-data/record-setting-auction
[link-18]: https://fiscaldata.treasury.gov/datasets/savings-bonds-securities/savings-bonds-securities
[link-19]: https://fiscaldata.treasury.gov/datasets/savings-bond-value-files/savings-bonds-value-files
[link-20]: https://fiscaldata.treasury.gov/datasets/schedules-federal-debt/schedules-of-federal-debt-by-month
[link-21]: https://fiscaldata.treasury.gov/datasets/schedules-federal-debt-daily/daily-activity
[link-22]: https://fiscaldata.treasury.gov/datasets/securities-issued-in-treasurydirect/sales
[link-23]: https://fiscaldata.treasury.gov/datasets/slgs-securities/state-and-local-government-series-securities-non-marketable
[link-24]: https://fiscaldata.treasury.gov/datasets/treasury-offset-program/federal-collections
[link-25]: https://fiscaldata.treasury.gov/datasets/treasury-report-on-receivables/treasury-report-on-receivables-full-data
[link-26]: https://fiscaldata.treasury.gov/datasets/treasury-reporting-rates-exchange/treasury-reporting-rates-of-exchange
[link-27]: https://fiscaldata.treasury.gov/datasets/revenue-collections-management/u-s-government-revenue-collections
[link-28]: https://fiscaldata.treasury.gov/datasets/monthly-statement-public-debt/summary-of-treasury-securities-outstanding
[link-29]: https://fiscaldata.treasury.gov/datasets/savings-bonds-issues-redemptions-maturities-by-series/paper-savings-bonds-issues-redemptions-and-maturities-by-series
[link-30]: https://fiscaldata.treasury.gov/datasets/status-report-government-gold-reserve/u-s-treasury-owned-gold
[link-31]: https://fiscaldata.treasury.gov/datasets/unemployment-trust-fund-yields/unemployment-trust-fund-quarterly-yields
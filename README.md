# ClicknClear Royalty Reporting Specification

# Rows

## Row Type
The first column for each row denotes the Row Type of row it is. The possible row types are as follows:

| Name           | Value
| -------- |-------------  |
| Total | T |
| Sales | S      |

## Income Type
The Second column for each row denotes the Income Type. The possible row types are as follows:
| Name                   | Value
| --------               |------ |
| Master Sale (Track)    | M     |
| Publishing Sale (Work) | P     |
| Producer Fee (Mix)     | PR    |

## Currency
The list of of supported Currencies are as follows:
| Name                 | Value
| --------             |------|
| Swiss Franc          | CHF  |
| Danish Krone         | DKK  |
| Euro                 | EUR  |
| British Pound        | GBP  |
| Norwegian Krone      | NOK  |
| Swedish Krona        | SEK  |
| United States Dollar | USD  |

For example:
- `T,M,..` - Master Totals Row
- `S,M,..` - Master Sales Row
- `P,T,..` - Publishing Totals Row
- `P,S,..` - Publishing Sales Row


## Total Row

The Total Row (T) has the same values for every Income Type and is as follows:

|             | Row Type                               | Income Type                                            | Start Of Reporting Period                                | End Of Reporting Period                                | Number of Sales Of this Income Type                                           | Currency                                                           | Balance Brought Forwards                                     | Amounts Due To Rightsholder                                           | Total Due To Rightsholder
| --------    | ----------                             | ----------                                             | ----------                                               | ----------                                             | ----------                                                                    | ----------                                                         | ----------                                                   | ----------                                                            | ----------
| Type        | [RowType](#row-type)                   | [IncomeType](#income-type)                             | ISO Date                                                 | ISO Date                                               | int                                                                           | Currency                                                           | float (4dp)                                                  | float (4dp)                                                           | float (2dp)
| Description | The [Row Type](#row-type)  of this row | The [Income Type](#income-type) this total row is for. | The Start of this reporting period as an ISO Date string | The End of this reporting period as an ISO Date string | The number of sales of this [IncomeType](#income-type) present in this report | The [Currency](#currency) the financial values of this line are in | The balance brought forwards from previous reporting periods | The amount due to the rightsholder generate for this reporting period | The final total due to the rightsholder for this reporting period and the previous balance brought forwards
| Example     | S                                      | M                                                      | 2023-01-01T00:00:00.000Z                                 | 2023-03-31T22:59:59.000Z                               | 10                                                                            | USD                                                                | 100.4220                                                     | 50.0881                                                               | 150.51

Raw example:
```
T,P,2023-01-01T00:00:00.000Z,2023-03-31T22:59:59.000Z,3.0000,USD,0.0000,288.5417,288.54
```

## Sales Row - Master

The values for [Row Type](#row-type) Sales (S) for [Income Type](#row-type) Master (M) is as follows:

|             | Row Type                               | Income Type                                            | Date Of Sale                              | Licensee Name                                                     |  Title                               | Performed By                                                          | ISRC                                    | UPC                                    | Label                                    | Territory Licensed                        | Gross Receipts                    | Refund                         | Sales Tax                           | Net Receipts                                                               | Distributable Recording Revenue                                      | License Margin                                                                    | Amount Due to Rightsholder                              |
| --------    | ----------                             | ----------                                             | ----------                                | ----------                                                        | ----------                           | ----------                                                            | ----------                              | ----------                             | ----------                               | ----------                                | ----------                        | ----------                     | ----------                          | ----------                                                                 | ----------                                                           | ----------                                                                        | ----------                                              |
| Type        | [RowType](#row-type)                   | [IncomeType](#income-type)                             | ISO Date                                  | String                                                            | String                               | String                                                                | String                                  | String                                 | String                                   | ISO 3166 Territory Code                   | float (4dp)                       | float (4dp)                    | float (4dp)                         | float (4dp)                                                                | float (4dp)                                                          | float (percent, 2dp)                                                              | float (4dp)                                             |
| Description | The [Row Type](#row-type)  of this row | The [Income Type](#income-type) this total row is for. | The date and time the sale was completed. | The full name of the licensee (team/individual) this sale is for. | The title of track this sale is for. | Comma Separated List of the performers of the track this sale is for. | The ISRC of the track this sale is for. | The UPC of the track this sale is for. | The Name of the label this track is for. | The Territory licensed this sale is for.  | The Gross Receipts for this sale. | The refund value for this sale | The sales tax applied to this sale. | The Net Receipts for this sale (Gross Receipts minus Sales Tax & Refunds). | The total distributable revenue for the master rights for this sale. | The license margin percentage the RH will receive from the distributable revenue. | The final amount due to the Rightsholder for this sale. |
| Example     | S                                      | M                                                      | 2023-01-01T00:00:00.000Z                  | Tristan Barlow-Griffin                                            | Track Title                          | Artist 1, Artist 2                                                    | USRC17607839                            | 00123456789012                         | Music Label                              | US                                        | 25.0000                           | 0.0000                         | 4.1666                              | 20.8333                                                                    | 10.4166                                                              | 70.00                                                                             | 7.2916                                                  |


## Sales Row - Publishing

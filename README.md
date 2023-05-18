# ClicknClear Royalty Reporting Specification
The following readme outlines the standard ClicknClear royalty reporting output which is available to all Rightsholders upon request.
All rows (outlined below) will be combined into a single .csv which is currently sent via email.
An example csv file called TEST_RIGHTSHOLDER_STANDARD_Q1_2023.csv can be found in this repo.

If you need any assistance with the implementation of this specification please contact [techteam@clicknclear.com](mailto:techteam@clicknclear.com).
For general royalty reporting queries please contact [royalty-reporting@clicknclear.com](mailto:royalty-reporting@clicknclear.com).

## Row Type
The first column for each row denotes the Row Type. The possible row types are as follows:

| Name  | Value
| ------|------ |
| Total | T     |
| Sales | S     |

## Income Type
The Second column for each row denotes the Income Type. The possible row types are as follows:
| Name                   | Value
| --------               |------ |
| Master Sale (Track)    | M     |
| Publishing Sale (Composition) | P     |
| Producer Fee (Mix)     | PR    |


## Row Type Combinations
For example:
- `T,M,..` - Master Totals Row
- `S,M,..` - Master Sales Row
- `P,T,..` - Publishing Totals Row
- `P,S,..` - Publishing Sales Row

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

## Total Row

The Total Row (T) has the same values for every Income Type and is as follows:

|             | Row Type                               | Income Type                                            | Start Of Reporting Period                                | End Of Reporting Period                                | Number of Sales Of this Income Type                                           | Currency                                                           | Balance Brought Forwards                                     | Amounts Due To Rightsholder                                           | Total Due To Rightsholder
| --------    | ----------                             | ----------                                             | ----------                                               | ----------                                             | ----------                                                                    | ----------                                                         | ----------                                                   | ----------                                                            | ----------
| Type        | [RowType](#row-type)                   | [IncomeType](#income-type)                             | ISO Date                                                 | ISO Date                                               | int                                                                           | Currency                                                           | float (4dp)                                                  | float (4dp)                                                           | float (2dp)
| Description | The [Row Type](#row-type)  of this row | The [Income Type](#income-type) this total row is for. | The Start of this reporting period as an ISO Date string | The End of this reporting period as an ISO Date string | The number of sales of this [IncomeType](#income-type) present in this report | The [Currency](#currency) the financial values of this line are in | The balance brought forwards from previous reporting periods | The amount due to the rightsholder generate for this reporting period | The final total due to the rightsholder for this reporting period and the balance brought forwards
| Example     | S                                      | M                                                      | 2023-01-01T00:00:00.000Z                                 | 2023-03-31T23:59:59.000Z                               | 10                                                                            | USD                                                                | 100.4220                                                     | 50.0881                                                               | 150.51

Raw example:
```
T,M,2023-01-01T00:00:00.000Z,2023-03-31T23:59:59.999Z,2,USD,100.0000,14.5832,114.58
```

## Sales Row - Master

The values for [Row Type](#row-type) Sales (S) for [Income Type](#row-type) Master (M) is as follows:

|             | Row Type                               | Income Type                                            | Date Of Sale                              | Licensee Name                                                     |  Title                               | Performed By                                                          | ISRC                                    | UPC                                    | Label                  | Territory Licensed                        | Currency                                                           | Gross Receipts                    | Refund                         | Sales Tax                           | Net Receipts                                                               | Distributable Recording Revenue                                      | License Margin                                                                    | Amount Due to Rightsholder                              |
| --------    | ----------                             | ----------                                             | ----------                                | ----------                                                        | ----------                           | ----------                                                            | ----------                              | ----------                             | ----------             | ----------                                | ----------                                                         | ----------                        | ----------                     | ----------                          | ----------                                                                 | ----------                                                           | ----------                                                                        | ----------                                              |
| Type        | [RowType](#row-type)                   | [IncomeType](#income-type)                             | ISO Date                                  | String                                                            | String                               | String                                                                | String                                  | String                                 | String                 | ISO 3166 Territory Code                   | Currency                                                           | float (4dp)                       | float (4dp)                    | float (4dp)                         | float (4dp)                                                                | float (4dp)                                                          | float (percent, 2dp)                                                              | float (4dp)                                             |
| Description | The [Row Type](#row-type) of this row  | The [Income Type](#income-type) this total row is for  | The date and time the sale was completed  | The full name of the licensee (team/individual) this sale is for  | The title of track this sale is for  | Comma Separated List of the performers of the track this sale is for  | The ISRC of the track this sale is for  | The UPC of the track this sale is for  | The Name of the label  | The Territory licensed this sale is for   | The [Currency](#currency) the financial values of this line are in | The Gross Receipts for this sale  | The refund value for this sale | The sales tax applied to this sale  | The Net Receipts for this sale (Gross Receipts minus Sales Tax & Refunds)  | The total distributable revenue for the master rights for this sale  | The license margin percentage the RH will receive from the distributable revenue  | The final amount due to the Rightsholder for this sale  |
| Example     | S                                      | M                                                      | 2023-01-01T00:00:00.000Z                  | Tristan Barlow-Griffin                                            | Track Title                          | Artist 1, Artist 2                                                    | USRC17607839                            | 00123456789012                         | Music Label            | US                                        | USD                                                                | 25.0000                           | 0.0000                         | 4.1666                              | 20.8333                                                                    | 10.4166                                                              | 70.00                                                                             | 7.2916                                                  |

Raw example:
```
S,M,2023-01-01T00:00:00.000Z,Tristan Barlow-Griffin,Track Title,"Artist 1, Artist 2",USRC17607839,00123456789012,Music Label,US,USD,25.0000,0.0000,4.1666,20.8333,10.4166,70.00,7.2916
```

## Sales Row - Publishing

The values for [Row Type](#row-type) Sales (S) for [Income Type](#row-type) Publishing (P) is as follows:

|             | Row Type                               | Income Type                                            | Date Of Sale                              | Licensee Name                                                     |  Title                                         | Performed By                                               | Writers                                                    | ISWC                        | Territory Licensed                        | Currency                                                           | Gross Receipts                    | Refund                         | Sales Tax                           | Net Receipts                                                               | Distributable Composition Revenue                                        | Composition Ownership                                                                                | Fee For Composition Share                                                                                        | License Margin                                                                    | Amount Due to Rightsholder                              |
| --------    | ----------                             | ----------                                             | ----------                                | ----------                                                        | ----------                                     | ----------                                                 | ----------                                                 | ----------                  | ----------                                | ----------                                                         | ----------                        | ----------                     | ----------                          | ----------                                                                 | ----------                                                               | ----------                                                                                           | ----------                                                                                                       | ----------                                                                        | ----------                                              |
| Type        | [RowType](#row-type)                   | [IncomeType](#income-type)                             | ISO Date                                  | String                                                            | String                                         | String                                                     | String                                                     | String                      | ISO 3166 Territory Code                   | Currency                                                           | float (4dp)                       | float (4dp)                    | float (4dp)                         | float (4dp)                                                                | float (4dp)                                                              | float (percent, 2dp)                                                                                 | float (4dp)                                                                                                      | float (percent, 2dp)                                                              | float (4dp)                                             |
| Description | The [Row Type](#row-type)  of this row | The [Income Type](#income-type) this total row is for  | The date and time the sale was completed  | The full name of the licensee (team/individual) this sale is for  | The title of the composition this sale is for  | Comma Separated List of the performers of the composition  | A Comma Separated list of the writers of the composition   | The ISWC of the composition | The Territory licensed this sale is for   | The [Currency](#currency) the financial values of this line are in | The Gross Receipts for this sale  | The refund value for this sale | The sales tax applied to this sale  | The Net Receipts for this sale (Gross Receipts minus Sales Tax & Refunds)  | The total distributable revenue for the publishing rights for this sale  | The controlling percentage ownership of this composition the Rightsholder has in the sold territory  | The amount of distributable revenue available to the Rightsholder based for their ownership of this composition  | The license margin percentage the RH will receive from the distributable revenue  | The final amount due to the Rightsholder for this sale  |
| Example     | S                                      | P                                                      | 2023-01-01T00:00:00.000Z                  | Tristan Barlow-Griffin                                            | Work Title                                     | Performer 1, Performer 2, Performer 3                      | Writer 1, Writer 2                                         | T3452468001                 | US                                        | USD                                                                | 25.0000                           | 0.0000                         | 4.1666                              | 20.8333                                                                    | 10.4166                                                                  | 50.00                                                                                                | 5.2083                                                                                                           | 70.00                                                                             | 3.6458                                                  |

Raw example:
```
S,P,2023-01-01T00:00:00.000Z,Tristan Barlow-Griffin,Work Title,"Performer 1, Performer 2, Performer 3","Writer 1, Writer 2",T3452468001,US,USD,25.0000,0.0000,4.1666,20.8333,10.4166,50.00,5.2083,70.00,3.6458
```


## Full File Example
```
T,M,2023-01-01T00:00:00.000Z,2023-03-31T23:59:59.999Z,2,USD,100.0000,14.5832,114.58
S,M,2023-01-01T00:00:00.000Z,Tristan Barlow-Griffin,Track Title,"Artist 1, Artist 2",USRC17607839,00123456789012,Music Label,US,USD,25.0000,0.0000,4.1666,20.8333,10.4166,70.00,7.2916
S,M,2023-01-01T00:00:00.000Z,Tristan Garlow-Briffin,Track Title,Artist 1,USRC17607839,00123456789012,Music Label,US,USD,25.0000,0.0000,4.1666,20.8333,10.4166,70.00,7.2916
T,P,2023-01-01T00:00:00.000Z,2023-03-31T23:59:59.999Z,2,USD,50.0000,7.2916,57.29
S,P,2023-01-01T00:00:00.000Z,Tristan Barlow-Griffin,Work Title,"Performer 1, Performer 2, Performer 3","Writer 1, Writer 2",T3452468001,US,USD,25.0000,0.0000,4.1666,20.8333,10.4166,50.00,5.2083,70.00,3.6458
S,P,2023-01-01T00:00:00.000Z,Tristan Garlow-Briffin,Work Title,Artist 1,"Writer 1, Writer 2",T3452468001,US,USD,25.0000,0.0000,4.1666,20.8333,10.4166,50.00,5.2083,70.00,3.6458

```

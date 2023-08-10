# Calculations

#### Country(Customer):
  TRIM( SPLIT( [Customer Country], "_", 2 ) )

#### Customer ID:
  TRIM( SPLIT( [Customer Country], "_", 1 ) )

#### Invoice Year:
  YEAR([Invoice Date])

#### Avg. Inventory 2021:
  ([Start Stock 2021] + [End Stock 2021]) * [Direct Costs] / 2

#### COGS Revenue Ratio:
  [Total COGS 2021]/[Revenue 2021]

#### Direct Costs:
  [Raw Material Cost] + [Factory Labor Costs] + [Factory Equipment Rent Costs]

#### End Stock 2021:
  [Start Stock 2021] - [Total Orders 2021]

#### Inventory Turnover 2021:
  [Total COGS 2021] / [Avg. Inventory 2021]

#### Pick Metric 1:
  CASE [Parameters].[Pick Metric 1]
  WHEN 'Units Sold 2020' THEN [Units Sold 2020]
  WHEN 'Total Orders 2021' THEN [Total Orders 2021]
  END

#### Pick Metric 2:
  CASE [Parameters].[Pick Metric 2]
  WHEN 'Revenue 2021' THEN SUM([Revenue 2021])
  WHEN 'Inventory Turnover 2021' THEN AVG([Inventory Turnover 2021])
  END

#### Profit 2020:
  [Revenue 2020] - [Total COGS 2020]

#### Profit-to-Revenue Ratio:
  [Profit 2020]/[Revenue 2020]

#### Revenue 2020:
  [Units Sold 2020] * [Retail Price]

#### Revenue 2020 Percent:
  SUM([Revenue 2020]) / TOTAL(SUM([Revenue 2020])) * 100

#### Revenue 2021:
  [Total Orders 2021] * [Retail Price]

#### Revenue 2021 Percent:
  SUM([Revenue 2021]) / TOTAL(SUM([Revenue 2021])) * 100

#### Revenue Percent Difference:
  [Revenue 2021 Percent] - [Revenue 2020 Percent]

#### Revenue Up or Down:
  IF [Revenue Percent Difference] > 0 THEN 'Up'
  ELSE 'Down'
  END

#### Total COGS 2020:
  ([Raw Material Cost] + [Factory Labor Costs] + [Factory Equipment Rent Costs]) * [Units Sold 2020]

#### Total COGS 2021:
  ([Raw Material Cost] + [Factory Labor Costs] + [Factory Equipment Rent Costs]) * [Total Orders 2021]

#### Total Orders 2021:
  { FIXED [Description] : SUM(IF [Invoice Year] = 2021 THEN [Quantity] END) }

#### Total Orders 2022:
  { FIXED [Description] : SUM(IF [Invoice Year] = 2022 THEN [Quantity] END) }

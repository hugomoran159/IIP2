---
title:  Review of Capital Required for Irish Residential Market
# We don't need to list individual CSVs as sources anymore,
# Evidence will pick up the housing_model_data source directory automatically.
---

# Introduction

Irish Institutional Property (IIP) has updated its bespoke analysis of the likely capital requirement to fund the construction, and ultimate ownership of residential output. This analysis builds on several recent publications, notably from - the Commission on Housing, Department of Finance and the Central Bank of Ireland. This literature is supplemented by market soundings and a high-level finance model commissioned by IIP.

We have examined:
* Development Finance: equity and debt to finance the construction of houses and apartments.

* Investment or Long-term ownership capital: to buy and own the completed residential units.

* Tenure, and the impact this has on funding capacity, including the impact that the state capital expenditure on housing can impact the total funding available for residential development.


# Development Finance to Build Houses and Apartments

We have looked at the development finance required  for 3 separate scenarios.  Firstly, 30,000 units which is close to the actual output achieved in 2024. Secondly, 2 medium-term scenarios – 42,500 and the 60,000 units referenced in the Programme for Government 2025 .

### Source of Development Finance Required (€m)


```sql sources_long_data
-- Reshape data from wide to long format for charting
select '30k Units' as Scenario, Source, Base_2024 as Value from housing_model_data.capital_sources_value where Source != 'Total'
UNION ALL
select '42k Units' as Scenario, Source, Scenario_50k as Value from housing_model_data.capital_sources_value where Source != 'Total'
UNION ALL
select '60k Units' as Scenario, Source, Scenario_60k as Value from housing_model_data.capital_sources_value where Source != 'Total'
```

<div>

<BarChart
    data={sources_long_data}
    x=Scenario
    y=Value
    series=Source
    stacked=true
    sort=false
    xAxisTitle="Output Scenario"
    yAxisTitle="Finance" 
    yFmt='€#,##0.0,"B"'
/>

</div>

** Key Issues: **

 As we examine the current housing finance market, it appears unlikely that sufficient finance would be available to deliver 60,000 residential units. 

** Alternatively, we can see how many units are financed by the state and private sectors... **

### Number of Units per Annum
<div>

```sql units_long_data
-- Reshape number_of_units data for charting
select '30k Units' as Scenario, Source, Base_2024 as Value from housing_model_data.number_of_units where Source != 'Total'
UNION ALL
select '42k Units' as Scenario, Source, Scenario_50k as Value from housing_model_data.number_of_units where Source != 'Total'
UNION ALL
select '60k Units' as Scenario, Source, Scenario_60k as Value from housing_model_data.number_of_units where Source != 'Total'
```

<BarChart 
    data={units_long_data}
    x=Scenario 
    y=Value 
    series=Source 
    stacked=true
    sort=false
    xAxisTitle="RESIDENTIAL UNITS P.A"
    yAxisTitle="Number of Units"
    yAxisFormat=",.0f"
    tooltipFormat=",.0f">
    <ReferenceLine x='30k Units' y=26348 x2='60k Units' y2=44245 color="warning" lineType=dashed lineWidth=2 hideValue=true label="Reliance on institutional finance" labelPosition=belowEnd/>
    <ReferencePoint x="30k Units" y=26348 label='26%' labelPosition=top labelColor="warning" />
    <ReferencePoint x="60k Units" y=44245 label='53%' labelPosition=top labelColor="warning" />
</BarChart>

</div>

* Private finance will deliver 47,000 of the 60,000, with 53% of units being financed by private institutional capital.

** Another perspective on the flow of development finance to the residential market. **

The following two perspectives highlight how finance flows from the providers of development finance to the ultimate owners of the houses and apartments.

### Development Finance to Purchaser Flow 

<Tabs>
    <Tab label="30,000 Units Scenario">

```sql sankey_finance_flow_data
SELECT
    Development_Finance AS source,
    Purchaser AS target,
    Value_M AS value
FROM sankey_data.finance_flows
```

<SankeyChart
    data={sankey_finance_flow_data}
    source=source
    target=target
    value=value
    title="The finance to build and buy/own 30,000 units"
    valueFmt='€#,##0"M"'
/>
    </Tab>
    <Tab label="60,000 Units Scenario">

```sql sankey_finance_flow_data
SELECT
    Development_Finance AS source,
    Purchaser AS target,
    Value_M AS value
FROM sankey_data.finance_flows
```

<SankeyChart
    data={sankey_finance_flow_data}
    source=source
    target=target
    value=value
    title="The finance to build and buy/own 60,000 units"
    valueFmt='€#,##0"M"'
/>
    </Tab>
</Tabs> 

** Key Issues: **

* The Private Rented Sector is not currently functioning with no PRS units completed in 2024, as evidenced by the lack of any institutional capital on the purchaser/owner side of the chart for the 30,000 units scenario.

# Development Finance and Tenure

There are several distinct types of housing tenure, each requiring funding of different types and from different sources. For example:

* Social Housing: Funded primarily by the state and owned by Local Authorities and Approved Housing Bodies.

* One-Off Builds: Mainly houses and funded by mortgages and individual savings.

* Private Housing: For Sale - Funded by private capital and owned by individuals. For Rent - the Private Rental Sector is funded by private capital and is rented out to individuals at the market rent. 

* Affordable Housing: The Housing Commission highlighted the middle four deciles of income earners ("Squeezed middle"), in need of some form of support to purchase or rent properties (sections 5 and 7 of Report of the Housing Commission). Essentially, the state needs to direct supply side subsidies make properties affordable to buy or rent. 

A diverse range of funding, from numerous sources, is required to deliver all of these tenures in large numbers. 

Let's examine how tenures are funded under three separate scenarios:

** Current Residential Development Finance Market **

1. 30,000 units: 2024 residential output of approximately 30,000 units (not that final expenditure and unit numbers not yet available for social and affordable delivery as at 11 March 2024).

2. 42,500 units: The maximum number of residential units that could be funded if the key challenges outlined below are not addressed. 

** Future Residential Development Finance Market **

3. 60,000 units: The maximum number of residential units that could be funded if the key challenges outlined below are not addressed.

### Implications by Tenure 

<Tabs>
    <Tab label="30,000 Units Scenario">

```sql three_stage_sankey_data_30k
-- Stage 1 Links: Development Finance -> Tenure
WITH finance_to_tenure AS (
    SELECT
        Development_Finance AS source,
        Tenure AS target,
        SUM(Capital) AS value
    FROM sankey_a.sankey_a
    -- Ensure links have value and valid nodes
    WHERE Capital > 0 AND Capital IS NOT NULL
      AND Tenure IS NOT NULL AND Tenure != ''
      AND Development_Finance IS NOT NULL AND Development_Finance != ''
    GROUP BY Development_Finance, Tenure
),
-- Stage 2 Links: Tenure -> Purchaser
tenure_to_purchaser AS (
     SELECT
        Tenure AS source,
        Purchaser AS target,
        SUM(Capital) AS value
    FROM sankey_a.sankey_a
    -- Ensure links have value and valid nodes
    WHERE Capital > 0 AND Capital IS NOT NULL
      AND Purchaser IS NOT NULL AND Purchaser != ''
      AND Tenure IS NOT NULL AND Tenure != ''
    GROUP BY Tenure, Purchaser
)
-- Combine all links
SELECT source, target, value FROM finance_to_tenure
UNION ALL
SELECT source, target, value FROM tenure_to_purchaser
```
<SankeyChart
    data={three_stage_sankey_data_30k}
    source=source
    target=target
    value=value
    title="Development Finance → Tenure → Purchaser Capital (€m)"
    valueFmt='€#,##0"M"'
    colorPallet={['#cf0d06','#eb5752','#e88a87']}
/>
    </Tab>
    <Tab label="42,500 Units Scenario">

```sql three_stage_sankey_data_42k
-- Create links between Development Finance → Tenure → Purchaser with tracking IDs for 60k scenario
WITH finance_to_tenure AS (
    SELECT 
        Development_Finance AS source,
        Tenure AS target,
        SUM(Capital) AS value
    FROM sankey_b.sankey_b -- Assuming this table holds 60k data
    WHERE Capital > 0
    GROUP BY Development_Finance, Tenure
),
tenure_to_purchaser AS (
    SELECT 
        Tenure AS source,
        Purchaser AS target,
        SUM(Capital) AS value
    FROM sankey_b.sankey_b -- Assuming this table holds 60k data
    WHERE Capital > 0
    GROUP BY Development_Finance, Tenure, Purchaser
)

-- Combine all links
SELECT source, target, value FROM finance_to_tenure
UNION ALL
SELECT source, target, value FROM tenure_to_purchaser
```

<SankeyChart
    data={three_stage_sankey_data_42k}
    source=source
    target=target
    value=value
    title="Development Finance → Tenure → Purchaser Capital (€m)"
    valueFmt='€#,##0"M"'
/>
    </Tab>
    <Tab label="60,000 Units Scenario">

```sql three_stage_sankey_data_60k
-- Create links between Development Finance → Tenure → Purchaser with tracking IDs for 60k scenario
WITH finance_to_tenure AS (
    SELECT 
        Development_Finance AS source,
        Tenure AS target,
        SUM(Capital) AS value
    FROM sankey_c.sankey_c -- Assuming this table holds 60k data
    WHERE Capital > 0
    GROUP BY Development_Finance, Tenure
),
tenure_to_purchaser AS (
    SELECT 
        Tenure AS source,
        Purchaser AS target,
        SUM(Capital) AS value
    FROM sankey_c.sankey_c -- Assuming this table holds 60k data
    WHERE Capital > 0
    GROUP BY Development_Finance, Tenure, Purchaser
)

-- Combine all links
SELECT source, target, value FROM finance_to_tenure
UNION ALL
SELECT source, target, value FROM tenure_to_purchaser
```

<SankeyChart
    data={three_stage_sankey_data_60k}
    source=source
    target=target
    value=value
    title="Development Finance → Tenure → Purchaser Capital (€m)"
    valueFmt='€#,##0"M"'
/>
    </Tab>
</Tabs>

** Key Issues: **

But there are several challenges in the Residential Development Finance Market that need to be addressed if significantly higher levels of output are to be achieved. 

* State funding is allocated primarily through either direct procurement or forwarded funding arrangements.

* Affordable Housing not being financed by private sources due to cost/viability issues, with neither the Corí Conaithe or the Secure Tenancy Affordable Rental Investment (STAR) Scheme delivering effectively at present.

* The Private Rental Sector (PRS) is not functioning and delivered no new residential units in 2024. 

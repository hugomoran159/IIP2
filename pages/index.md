---
title:  Review of capital flows necessary to fund the requirements of the Irish Residential Market
# We don't need to list individual CSVs as sources anymore,
# Evidence will pick up the housing_model_data source directory automatically.
---

<script>
const myColorMap = {
    // Funding Sources / Purchasers (Colors from Image)
    'State Funding': '#A5CDEE',         // Dark Blue (like Google)
    'State': '#A5CDEE',
    'Private (Domestic)': '#44A1BF',   // Gold/Orange (like Twitter)
    'Domestic': '#44A1BF',
    'Private (Institutional)': '#226AA4', // Green/Teal (like '/')
    'Institutional': '#226AA4',
    'Private Individuals': '#44A1BF',   // Light Blue (like Direct)

    // Tenures (Colors from Image)
    'Social Housing': '#8DACBF',          // Maroon/Red (like LinkedIn)
    'One-Off Builds': '#85C7C6',        // Beige/Tan (like Tiktok)
    'Affordable for Sale': '#D2C6AC',    // Bright Blue/Cyan (like Pinterest/Bing)
    'Private for Sale': '#46A486',        // Muted Blue/Grey (like Facebook)
    'Affordable Cost Rental': '#8F3D56', // Teal/Cyan (like Bing/Blog)
    'Private Rental Sector (PRS)': '#F4B548' // Dark Blue (like Google - REUSED)
};
</script>
# Introduction

Irish Institutional Property (IIP) has updated its analysis of the likely capital requirement to fund the construction, and ultimate ownership of residential output, based on data from detailed industry engagement. This analysis builds on several recent publications, notably from - the Commission on Housing, Department of Finance and the Central Bank of Ireland. This literature is supplemented by market soundings and a high-level finance model commissioned by IIP. To understand how the market functions and the critical interplay between development funding, viability based on affordability and long term funding we examine 3 key areas:

* Development Finance: equity and debt to finance the construction of houses and apartments.

* Investment or Long-term ownership capital: to buy and own the completed residential units.

* Tenure & Affordability, and the impact this has on the ability to scale overall housing output numbers. Overall housing output can only scale from current levels if the end user can afford to rent or buy new housing. Highlighting the critical importance of using state capital expenditure to leverage (unlock?) private funding to the total funding available for residential development is in place for all tenures.

# Development Finance to Build Houses and Apartments

We have looked at the development finance required  for 3 separate scenarios.  Firstly, 30,000 units which is close to the actual output achieved in 2024. Secondly, 2 medium-term scenarios – 42,500, the theoretical maximum number of residential units that could be funded if the key challenges outlined below are not addressed, and the 60,000 units referenced in the Programme for Government 2025 .

## Source of Development Finance Required (€m)


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
    seriesOrder={['State Funding', 'Private (Domestic)', 'Private (Institutional)']}
    echartsOptions={{
        color: ['#A5CDEE', '#44A1BF', '#226AA4']
    }}
/>

</div>

** Key Issues: **

 As we examine the current housing finance market, it appears unlikely that sufficient finance would be available to deliver 60,000 residential units. 

* State. It is assumed that the state capital allocation to Housing is near the upper limit, both historically and relative to other EU/OECD members. Budget 2025 allocates €6.1bn: capital funding €3.2bn, Land Development Agency €1.25bn and Housing Finance Agency €1.65bn.
* Private Finance. The balance of the financerequired to develop 60,000 units (€26.3bn??) is significant, requiring 80% of all funding to come from private sources 
* Challenges. Insufficient private finance is being attracted to aid the delivery of affordable housing alongside state funding and the complete lack of a functioning PRS sector.


** Alternatively, we can see how many units are financed by the state and private sectors... **

## Number of Units per Annum
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
    tooltipFormat=",.0f"
    seriesOrder={['State Funding', 'Private (Domestic)', 'Private (Institutional)']}
    echartsOptions={{
        color: ['#A5CDEE', '#44A1BF', '#226AA4'], // Base colors
        series: [
            {}, // Config for 'State Funding' (uses defaults)
            {}, // Config for 'Private (Domestic)' (uses defaults)
            {   // Config for 'Private (Institutional)' (index 2)
                markLine: {
                    symbol: ['none', 'arrow'], // Arrow at the end
                    precision: 0, // Use integer coords
                    label: {
                        show: true,
                        position: 'middle', // Or 'start', 'end'
                        formatter: 'Reliance on Institutional Finance (26% -> 53%)' // Combined label
                    },
                    lineStyle: {
                        color: '#ff9900', // Orange-like color
                        type: 'dashed',
                        width: 2
                    },
                    data: [
                        // Define the line segment using coordinates
                        [ // A single line segment is an array of two points
                            { coord: ['30k Units', 26348] },
                            { coord: ['60k Units', 44245] }
                        ]
                    ]
                }
            }
        ]
    }}>
</BarChart>

</div>

* Private finance will need to deliver 47,000 of the 60,000, which includes affordable units with 53% of units being financed by private institutional capital.

** Another perspective on the flow of development finance to the residential market. **

The following two perspectives highlight how finance flows from the providers of development finance to the ultimate owners of the houses and apartments.

## Development Finance to Purchaser Flow 

<Tabs>
    <Tab label="30,000 Units Scenario">

```sql sankey_finance_flow_data_30k
SELECT
    Development_Finance AS source,
    Purchaser AS target,
    Value_M AS value
FROM sankey_data.small
```

<SankeyChart
    data={sankey_finance_flow_data_30k}
    source=source
    target=target
    value=value
    title="The finance to build and buy/own 30,000 units"
    valueFmt='€#,##0"M"'
    echartsOptions={{
        series: [{
            data: [
                { name: 'Private (Institutional)', itemStyle: { color: '#226AA4' } },
                { name: 'Private (Domestic)', itemStyle: { color: '#44A1BF' } },
                { name: 'Private Individuals', itemStyle: { color: '#44A1BF' } },
                { name: 'State Funding', itemStyle: { color: '#A5CDEE' } },
                { name: 'State', itemStyle: { color: '#A5CDEE' } }
            ]
        }]
    }}
/>
    </Tab>
    <Tab label="60,000 Units Scenario">

```sql sankey_finance_flow_data_60k
SELECT
    Development_Finance AS source,
    Purchaser AS target,
    Value_M AS value
FROM sankey_data.large
```

<SankeyChart
    data={sankey_finance_flow_data_60k}
    source=source
    target=target
    value=value
    title="The finance to build and buy/own 60,000 units"
    valueFmt='€#,##0"M"'
    echartsOptions={{
        series: [{
            data: [
                { name: 'Private (Institutional)', itemStyle: { color: '#226AA4' } },
                { name: 'Institutional', itemStyle: { color: '#226AA4' } },
                { name: 'Private (Domestic)', itemStyle: { color: '#44A1BF' } },
                { name: 'Private Individuals', itemStyle: { color: '#44A1BF' } },
                { name: 'State Funding', itemStyle: { color: '#A5CDEE' } },
                { name: 'State', itemStyle: { color: '#A5CDEE' } } 
            ]
        }]
    }}
/>
    </Tab>
</Tabs> 

** Key Issues: **

* The Private Rented Sector is not currently functioning with no PRS units completed in 2024, as evidenced by the lack of any institutional capital on the purchaser/owner side of the chart for the 30,000 units scenario.

* The imposition of a 2% rent cap has been a key determinant of this decline. The rate of growth is below the level that is required to be competitive in attracting investment by pension funds as it is less than the annual growth in return that is required by managers to ensure that they can match growth in liabilities, as approximated by increases in incomes, with expected returns.

# Development Finance and Tenure

There are several distinct types of housing tenure, each requiring funding of different types and from different sources. For example:

* Social Housing: Funded primarily by the state and owned by Local Authorities and Approved Housing Bodies.

* One-Off Builds: Mainly houses and funded by mortgages and individual savings.

* Private Housing: For Sale - Funded by private capital and owned by individuals. For Rent - the Private Rental Sector is funded by private capital and is rented out to individuals at the market rent. 

* Affordable Housing: The Housing Commission highlighted the middle four deciles of income earners ("Squeezed middle"), in need of some form of support to purchase or rent properties (sections 5 and 7 of Report of the Housing Commission). Essentially, the state needs to direct supply side subsidies make properties affordable to buy or rent, but to optimise output in this section the state needs to use its capital to "crowd in" private institutional captial rather than trying to do this on itts own. The required output can never be met without a viable strategy of this nature. 

A diverse range of funding, from numerous sources, is required to deliver all of these tenures in large numbers. 

Let's examine how tenures are funded under **three separate scenarios**:

** Current Residential Development Finance Market **

1. 30,000 units: 2024 residential output of approximately 30,000 units (not that final expenditure and unit numbers not yet available for social and affordable delivery as at 11 March 2024).

2. 42,500 units: The theoretical maximum number of residential units that could be funded if the key challenges outlined below are not addressed. 

** Future Residential Development Finance Market **

3. 60,000 units: The maximum number of residential units that could be funded if the key challenges outlined below are not addressed satisfactorily.

## Implications by Tenure 

<Tabs>
    <Tab label="30,000 Units Scenario">

```sql three_stage_sankey_data_30k
-- Stage 1 Links: Development Finance -> Tenure
WITH finance_to_tenure AS (
    SELECT
        Development_Finance AS source,
        Tenure AS target,
        -- Sum capital only for the Finance->Tenure stage from original data
        SUM(Capital) AS value
    FROM sankey_a.sankey_a -- Use original data for this stage
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
        -- Sum capital only for the Tenure->Purchaser stage from new data
        SUM(CAST(Capital AS DOUBLE)) AS value -- Cast Capital to DOUBLE
    FROM sankey_a.sankey_a_purchaser -- Corrected data source name back
    -- Ensure links have value and valid nodes
    WHERE CAST(Capital AS DOUBLE) > 0 AND Capital IS NOT NULL
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
    echartsOptions={{
        series: [{
            data: [
                { name: 'Private (Institutional)', itemStyle: { color: '#226AA4' } },
                { name: 'Private (Domestic)', itemStyle: { color: '#44A1BF' } },
                { name: 'Private Individuals', itemStyle: { color: '#44A1BF' } },
                { name: 'Private For Sale', itemStyle: { color: '#46A486' } },
                { name: 'One-Off Builds', itemStyle: { color: '#85C7C6' } },
                { name: 'Affordable For Sale', itemStyle: { color: '#D2C6AC' } },
                { name: 'Affordable Cost Rental', itemStyle: { color: '#8F3D56' } },
                { name: 'Social Housing', itemStyle: { color: '#8DACBF' } },
                { name: 'State', itemStyle: { color: '#A5CDEE' } },
                { name: 'State Funding', itemStyle: { color: '#A5CDEE' } }
            ]
        }]
    }}
/>
    </Tab>
    <Tab label="42,500 Units Scenario">

```sql three_stage_sankey_data_42k
-- Create links between Development Finance -> Tenure -> Purchaser with tracking IDs for 60k scenario
WITH finance_to_tenure AS (
    SELECT 
        Development_Finance AS source,
        Tenure AS target,
        -- Sum capital only for the Finance->Tenure stage from original data
        SUM(Capital) AS value
    FROM sankey_b.sankey_b -- Use original data for this stage
    WHERE Capital > 0
    GROUP BY Development_Finance, Tenure
),
tenure_to_purchaser AS (
    SELECT 
        Tenure AS source,
        Purchaser AS target,
        -- Sum capital only for the Tenure->Purchaser stage from new data
        SUM(CAST(Capital AS DOUBLE)) AS value -- Cast Capital to DOUBLE
    FROM sankey_b.sankey_b_purchaser -- Corrected data source name back
    WHERE CAST(Capital AS DOUBLE) > 0 -- Cast Capital in WHERE clause
    GROUP BY Tenure, Purchaser
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
    echartsOptions={{
        series: [{
            data: [
                { name: 'Private (Institutional)', itemStyle: { color: '#226AA4' } },
                { name: 'Private (Domestic)', itemStyle: { color: '#44A1BF' } },
                { name: 'Private Individuals', itemStyle: { color: '#44A1BF' } },
                { name: 'Private For Sale', itemStyle: { color: '#46A486' } },
                { name: 'One-Off Builds', itemStyle: { color: '#85C7C6' } },
                { name: 'Affordable For Sale', itemStyle: { color: '#D2C6AC' } },
                { name: 'Affordable Cost Rental', itemStyle: { color: '#8F3D56' } },
                { name: 'Social Housing', itemStyle: { color: '#8DACBF' } },
                { name: 'State Funding', itemStyle: { color: '#A5CDEE' } },
                { name: 'State', itemStyle: { color: '#A5CDEE' } }
 
            ]
        }]
    }}
/>
    </Tab>
    <Tab label="60,000 Units Scenario">

```sql three_stage_sankey_data_60k
-- Create links between Development Finance -> Tenure -> Purchaser for 60k scenario
WITH finance_to_tenure AS (
    SELECT 
        Development_Finance AS source,
        Tenure AS target,
        -- Sum capital only for the Finance->Tenure stage from original data
        SUM(Capital) AS value
    FROM sankey_c.sankey_c -- Use original data for this stage
    WHERE Capital IS NOT NULL AND CAST(Capital AS DOUBLE) > 0 -- Ensure capital is numeric and > 0
    GROUP BY Development_Finance, Tenure
),
tenure_to_purchaser AS (
    SELECT 
        Tenure AS source,
        Purchaser AS target,
        -- Sum capital only for the Tenure->Purchaser stage from new data
        SUM(CAST(Capital AS DOUBLE)) AS value -- Cast Capital to DOUBLE
    FROM sankey_c.sankey_c_purchaser -- Use NEW data for this stage
    WHERE Capital IS NOT NULL AND CAST(Capital AS DOUBLE) > 0 -- Cast Capital in WHERE clause
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
    data={three_stage_sankey_data_60k}
    source=source
    target=target
    value=value
    title="Development Finance → Tenure → Purchaser Capital (€m)"
    valueFmt='€#,##0"M"'
    echartsOptions={{
        series: [{
            data: [
                { name: 'Private (Institutional)', itemStyle: { color: '#226AA4' } },
                { name: 'Institutions', itemStyle: { color: '#226AA4' } },
                { name: 'Private For Rent (PRS)', itemStyle: { color: '#F4B548' } },
                { name: 'Private For Sale', itemStyle: { color: '#46A486' } },     
                { name: 'Private (Domestic)', itemStyle: { color: '#44A1BF' } },
                { name: 'Private Individuals', itemStyle: { color: '#44A1BF' } },
                { name: 'One-Off Builds', itemStyle: { color: '#85C7C6' } },
                { name: 'Affordable For Sale', itemStyle: { color: '#D2C6AC' } },
                { name: 'Affordable Cost Rental', itemStyle: { color: '#8F3D56' } },
                { name: 'Social Housing', itemStyle: { color: '#8DACBF' } },
                { name: 'State Funding', itemStyle: { color: '#A5CDEE' } },
                { name: 'State', itemStyle: { color: '#A5CDEE' } }, 
            ]
        }]
    }}
/>
    </Tab>
</Tabs>

** Key Issues: **

But there are several challenges in the Residential Development Finance Market that need to be addressed if significantly higher levels of output are to be achieved. 

* State funding is allocated primarily through either direct procurement or forwarded funding arrangements.

* Affordable Housing not being financed by private sources due to cost/viability issues, without a subsidy with neither the Corí Conaithe or the Secure Tenancy Affordable Rental Investment (STAR) Scheme working effectively at present, as they have not addressed key concerns of private finance.

* The Private Rental Sector (PRS) is not functioning and delivered no new residential units in 2024. While the interest rate and construction inflaction shocks would have tempered supply, rent increases have by now compensated for the inflation and interst rates are normalising. The primary reason for the lack of investment in the sector now is the 2% rent cap and its failure to offer investors an appropriate hedge to the investment requirements of their beneficiaries - often just normal pension holders.  

## Development Finance by Tenure

```sql dev_finance_by_tenure_combined
-- Combine 30k and 60k scenarios and create a combined x-axis category
WITH combined_data AS (
    SELECT
        '30k Units' as Scenario,
        Tenure,
        Development_Finance AS Source,
        SUM(try_cast(Capital AS DOUBLE)) AS Value -- Use try_cast
    FROM sankey_a.sankey_a
    WHERE try_cast(Capital AS DOUBLE) > 0 -- Filter using try_cast
    GROUP BY Scenario, Tenure, Development_Finance
    UNION ALL
    SELECT
        '60k Units' as Scenario,
        Tenure,
        Development_Finance AS Source,
        SUM(try_cast(Capital AS DOUBLE)) AS Value -- Use try_cast
    FROM sankey_c.sankey_c -- Assuming sankey_c corresponds to 60k
    WHERE try_cast(Capital AS DOUBLE) > 0 -- Filter using try_cast
    GROUP BY Scenario, Tenure, Development_Finance
)
SELECT
    (Source || ' - ' || Scenario) AS SourceScenario,
    Tenure,
    Value,
    -- Add columns for ordering if needed
    CASE Source
        WHEN 'State Funding' THEN 1
        WHEN 'Private (Domestic)' THEN 2
        WHEN 'Private (Institutional)' THEN 3
        ELSE 4
    END AS source_order,
    CASE Scenario
        WHEN '30k Units' THEN 1
        WHEN '60k Units' THEN 2
        ELSE 3
    END AS scenario_order
FROM combined_data
ORDER BY scenario_order, source_order
```

<BarChart
    data={dev_finance_by_tenure_combined}
    x=SourceScenario
    y=Value
    series=Tenure
    stacked=true
    sort=false
    title="Development Finance by Tenure (30k vs 60k Units)"
    xAxisTitle="Source of Finance - Scenario"
    yAxisTitle="Development Finance (€m)"
    yFmt='€#,##0"M"'
    seriesOrder={['Social Housing', 'One-Off Builds', 'Affordable For Sale', 'Private For Sale', 'Affordable Cost Rental', 'Private for Rent (PRS)']}
    xLabelWrap=true
    echartsOptions={{
        color: ['#F4B548', '#8DACBF', '#85C7C6', '#D2C6AC', '#46A486','#8F3D56']
    }}
/>
---
title: Irish Housing Funding Model
# We don't need to list individual CSVs as sources anymore,
# Evidence will pick up the housing_model_data source directory automatically.
---
This report provides an overview of a model simulating Irish housing funding requirements based on different output scenarios. 

## Model Assumptions

The following tables outline the key assumptions used as inputs to the model.


### Development Costs (€)

This table shows the estimated base cost per unit for different dwelling types.

```sql dev_costs_data
select 
    Dept_Housing_MMcD,
    Base_Year,
    Base_Cost,
    Inflation_Percent,
    Cost_per_unit
from housing_model_data.development_costs
```

<DataTable data={dev_costs_data} hideExplorer=true>
    <Column id="Dept_Housing_MMcD" title="Dwelling Type" />
    <Column id="Base_Year" title="Base Year" align="center"/>
    <Column id="Base_Cost" title="Base Cost (€)" format="eur:,.0f" align="right"/>
    <Column id="Inflation_Percent" hide=true />
    <Column id="Cost_per_unit" title="Cost per Unit (€)" format="eur:,.0f" align="right"/>
</DataTable>


### Debt / Equity Requirements (%)

This table outlines the assumed mix of debt and equity financing for different build types.

```sql debt_equity_data
select 
    Category,
    Equity_Percent,
    Debt_Percent,
    Notes
from housing_model_data.debt_equity_requirements
```

<DataTable data={debt_equity_data} hideExplorer=true>
    <Column id="Category" title="Category" />
    <Column id="Equity_Percent" title="Equity %" format="pct" align="center"/>
    <Column id="Debt_Percent" title="Debt %" format="pct" align="center"/>
    <Column id="Notes" title="Notes" />
</DataTable>


### House / Apartment Mix (%)

This table shows the assumed percentage split between houses and apartments in the modelled output scenarios.

```sql house_mix_data
select 
    Category,
    Percent
from housing_model_data.house_apartment_mix
```

<DataTable data={house_mix_data} hideExplorer=true>
    <Column id="Category" title="Category" />
    <Column id="Percent" title="%" format="pct" align="center"/>
</DataTable>


## Model Workings & Outputs

### Completions (Units)

This table shows the projected unit completions under different output scenarios.

```sql completions_data
select
    Item,
    Base_2024,
    Scenario_50k,
    Scenario_60k
from housing_model_data.completions
```

<DataTable data={completions_data} hideExplorer=true>
    <Column id=Item title=""/>
    <Column id=Base_2024 title="30k Scenario" format=",.0f" align="right"/>
    <Column id=Scenario_50k title="50k Scenario" format=",.0f" align="right"/>
    <Column id=Scenario_60k title="60k Scenario" format=",.0f" align="right"/>
</DataTable>


### Finance Requirement (€m)

These tables detail the calculated finance requirements.

#### Capital Expenditure (Gross)

```sql capital_exp_data
select
    Item,
    Base_2024,
    Scenario_50k,
    Scenario_60k
from housing_model_data.capital_expenditure
```

<DataTable data={capital_exp_data} hideExplorer=true>
    <Column id=Item title=""/>
    <Column id=Base_2024 title="30k Scenario (€m)" format="eur:,.0f" align="right"/>
    <Column id=Scenario_50k title="50k Scenario (€m)" format="eur:,.0f" align="right"/>
    <Column id=Scenario_60k title="60k Scenario (€m)" format="eur:,.0f" align="right"/>
</DataTable>


#### Development Finance

```sql dev_finance_output_data
select
    Item,
    Base_2024,
    Scenario_50k,
    Scenario_60k
from housing_model_data.development_finance
```

<DataTable data={dev_finance_output_data} hideExplorer=true>
    <Column id=Item title=""/>
    <Column id=Base_2024 title="30k Scenario (€m)" format="eur:,.0f" align="right"/>
    <Column id=Scenario_50k title="50k Scenario (€m)" format="eur:,.0f" align="right"/>
    <Column id=Scenario_60k title="60k Scenario (€m)" format="eur:,.0f" align="right"/>
</DataTable>


#### TOTAL FINANCE REQUIREMENT

```sql total_req_data
select
    Category,
    Base_2024,
    Scenario_50k,
    Scenario_60k
from housing_model_data.total_finance_requirement
```

<DataTable data={total_req_data} hideExplorer=true>
    <Column id=Category title=""/>
    <Column id=Base_2024 title="30k Scenario (€m)" format="eur:,.0f" align="right"/>
    <Column id=Scenario_50k title="50k Scenario (€m)" format="eur:,.0f" align="right"/>
    <Column id=Scenario_60k title="60k Scenario (€m)" format="eur:,.0f" align="right"/>
</DataTable>


### Source of Development Finance

```sql sources_long_data
-- Reshape data from wide to long format for charting
select '30k Units' as Scenario, Source, Base_2024 as Value from housing_model_data.capital_sources_value where Source != 'Total'
UNION ALL
select '50k Units' as Scenario, Source, Scenario_50k as Value from housing_model_data.capital_sources_value where Source != 'Total'
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
    title="Source of Development Finance Required (€m)"
    xAxisTitle="Output Scenario"
    yAxisTitle="Finance" 
    yFmt='€#,##0.0,"B"'
/>

</div>
### Number of Units / Sources of Capital


<div>

```sql units_long_data
-- Reshape number_of_units data for charting
select '30k Units' as Scenario, Source, Base_2024 as Value from housing_model_data.number_of_units where Source != 'Total'
UNION ALL
select '50k Units' as Scenario, Source, Scenario_50k as Value from housing_model_data.number_of_units where Source != 'Total'
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
    title="Number of Units per Annum"
    xAxisTitle="RESIDENTIAL UNITS P.A"
    yAxisTitle="Number of Units"
    yAxisFormat=",.0f"
    tooltipFormat=",.0f">
    <ReferenceLine x='30k Units' y=26348 x2='60k Units' y2=44245 color="warning" lineType=dashed lineWidth=2 hideValue=true label="Reliance on institutional finance" labelPosition=belowEnd/>
    <ReferencePoint x="30k Units" y=26348 label='26%' labelPosition=top labelColor="warning" />
    <ReferencePoint x="60k Units" y=44245 label='53%' labelPosition=top labelColor="warning" />

</BarChart>

</div>

<div>

#### Sources of Capital (€m)
```sql sources_value_table
select * from housing_model_data.capital_sources_value
```
<DataTable data={sources_value_table} hideExplorer=true>
    <Column id=Source title=""/>
    <Column id=Base_2024 title="€m" format="eur:,.0f" align="right"/>
    <Column id=Scenario_50k title="€m" format="eur:,.0f" align="right"/>
    <Column id=Scenario_60k title="€m" format="eur:,.0f" align="right"/>
</DataTable>

#### Sources of Capital (%)
```sql sources_pct_table
select * from housing_model_data.capital_sources_percent
```
<DataTable data={sources_pct_table} hideExplorer=true>
    <Column id=Source title=""/>
    <Column id=Base_2024 title="%" format=".0%" align="right"/>
    <Column id=Scenario_50k title="%" format=".0%" align="right"/>
    <Column id=Scenario_60k title="%" format=".0%" align="right"/>
</DataTable>

#### Number of Units
```sql units_table
select * from housing_model_data.number_of_units
```
<DataTable data={units_table} hideExplorer=true>
    <Column id=Source title=""/>
    <Column id=Base_2024 title="Units" format=",.0f" align="right"/>
    <Column id=Scenario_50k title="Units" format=",.0f" align="right"/>
    <Column id=Scenario_60k title="Units" format=",.0f" align="right"/>
</DataTable>

</div>



### Development Finance to Purchaser Flow (60k Units Scenario, €m)

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

### Implications by Tenure (60k Units Scenario, €m)

```sql three_stage_sankey_data
-- Create links between Development Finance → Tenure and Tenure → Purchaser
-- First union: Development Finance to Tenure links
SELECT 
    Development_Finance AS source,
    Tenure AS target,
    SUM(Capital) AS value
FROM sankey_three_stage.sankey2
WHERE Capital > 0
GROUP BY Development_Finance, Tenure

UNION ALL

-- Second union: Tenure to Purchaser links
SELECT 
    Tenure AS source,
    Purchaser AS target,
    SUM(Capital) AS value
FROM sankey_three_stage.sankey2
WHERE Capital > 0
GROUP BY Tenure, Purchaser
```

<SankeyChart
    data={three_stage_sankey_data}
    source=source
    target=target
    value=value
    title="Development Finance → Tenure → Purchaser Capital (€m)"
    valueFmt='€#,##0"M"'
/>
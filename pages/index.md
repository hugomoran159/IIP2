---
title: Development Finance Flows
sources:
    dev_finance: sources/Development Finance.csv
---

# Development Finance Flows (€m)

This Sankey diagram shows the flow of development finance from different sources to various purchasers.

```sql source_data
with base_data as (
    select 
        "Development Finance" as source, 
        "Purchaser" as target,
        "€m" as value 
    from IIP.dev_fin
),
source_totals as (
    select
        source,
        sum(value) as total_source_value
    from base_data
    group by source
),
target_totals as (
    select
        target,
        sum(value) as total_target_value
    from base_data
    group by target
),
calcs as (
    select 
        b.source, 
        b.target,
        b.value,
        -- Calculate percentages separately
        round(b.value / s.total_source_value * 100, 1) as pct_of_source,
        round(b.value / t.total_target_value * 100, 1) as pct_of_target,
        s.total_source_value,
        t.total_target_value
    from base_data b
    join source_totals s on b.source = s.source
    join target_totals t on b.target = t.target
)
select
    source,
    target,
    value,
    -- Construct the final tooltip string
    source || ' → ' || target || ': ' || value::varchar || ' €m (' || 
    pct_of_source::varchar || '% of ' || source || ' total, ' ||
    pct_of_target::varchar || '% of ' || target || ' total)' as tooltip_label
from calcs
```

<SankeyChart 
    data={source_data} 
    source=source 
    target=target 
    value=value
    tooltip=tooltip_label 
    title="Development Finance Flows"
/>

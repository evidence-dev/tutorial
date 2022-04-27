# {$page.params.product}

```monthly_item_sales
select
order_month,
item,
count(*) as units_sold

from orders
group by order_month,item
```

```item_sales_by_price
select 
item,
sales as price_usd,
count(sales) as units_sold
from orders

group by item, price_usd
```

<BarChart 
    title='Orders per week'
    data={data.monthly_item_sales.filter(d => d.item === $page.params.product)} 
    x=order_month 
    y=units_sold
/>

<AreaChart
    title='Price Distribution of Sales'
    data={data.item_sales_by_price.filter(d => d.item === $page.params.product)} 
    x=price_usd
    y=units_sold
    xAxisTitle='Sales Price'
    yAxisTitle='Units Sold'
/>
# Business Performance
Below is a summary of Needful Things' sales.

## Monthly Orders
```monthly_orders
select
    order_month,
    count(*) as orders
from orders

group by order_month
order by order_month desc
```

The most recent month of data began <Value data={data.monthly_orders} fmt=date/>, 
when there were <Value data={data.monthly_orders} column=orders/> orders.

<LineChart 
    data={data.monthly_orders} 
    title='Needful Things Inc. Monthly Orders'
    x=order_month
    y=orders
/>

## Product Performance
```product_performance
select
    item,
    sum(sales) as item_sales
from orders

group by item
order by item_sales desc
```

Items ranked by sales are as follows:

{#each data.product_performance as prod_perf}

* [{prod_perf.item}](/product/{prod_perf.item}): <Value value={prod_perf.item_sales} fmt=usd/>

{/each}
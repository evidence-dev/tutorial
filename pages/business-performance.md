# Business Performance
Below is a summary of Needful Things' sales.

```monthly_orders

select
    order_month, 
    count(sales) as orders,
    sum(sales) as sales_usd,
    sum(sales) / count (sales) as basket_size_usd
from orders
group by order_month
order by order_month desc
```

The most recent month of data began <Value data={monthly_orders} fmt=date/>, 
when there were <Value data={monthly_orders} column=orders/> orders.

## Monthly Sales
<AreaChart 
    data={monthly_orders} 
    x=order_month
    y=sales_usd
/>

## Monthly Orders
<LineChart 
    data={monthly_orders} 
    x=order_month
    y=orders
/>

## Basket Size
<BarChart 
    data={monthly_orders} 
    x=order_month
    y=basket_size_usd
/>
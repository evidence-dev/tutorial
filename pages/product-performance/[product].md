# {$page.params.product}

```monthly_item_sales
select
order_month,
item,
count(*) as orders

from orders
group by order_month,item
```

<BarChart 
    title='Orders per week'
    data={monthly_item_sales.filter(d => d.item === $page.params.product)} 
    x=order_month 
    y=orders
/>
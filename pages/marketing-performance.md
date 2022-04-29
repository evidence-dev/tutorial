# Marketing Performance

## Orders by Channel

```orders_by_channel
select 
channel,
order_month,
channel_month,
count(*) as orders

from orders
group by channel, order_month
order by orders
```

<AreaChart
    data={data.orders_by_channel}
    x=order_month
    y=orders
    series=channel
/>

## Channel CPA
```channel_cpa
select 
marketing_channel,
sum(spend) as total_spend,
sum(orders) as total_orders,
sum(spend) / sum(orders) as cpa

from marketing_spend
left join ${orders_by_channel} using(channel_month)

group by marketing_channel
order by cpa
```

## CPA by Channel
{#each data.channel_cpa as channel}

**{channel.marketing_channel} CPA was <Value value={channel.cpa} fmt=usd/>**, with a spend of <Value value={channel.total_spend} fmt=usd/>, bringing in <Value value={channel.total_orders}/> orders.

{/each}
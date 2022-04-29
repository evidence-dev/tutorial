# Products

```product_list
select 
item
from orders
group by item
```

{#each data.product_list as product}
    
[{product.item}](/product-performance/{product.item})

{/each}
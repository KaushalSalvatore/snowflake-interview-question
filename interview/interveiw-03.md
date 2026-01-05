#### Q-1 Write a query to list the top 5 most frequently occurring values in a column ?

```console
SELECT 
    product_id, 
    COUNT(*) AS frequency
FROM 
    sales
GROUP BY 
    product_id
ORDER BY 
    frequency DESC
LIMIT 5;

```
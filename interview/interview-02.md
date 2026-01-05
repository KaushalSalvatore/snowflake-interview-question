#### Q-1 How to clone a table ?

```console
CREATE TABLE cust_clone CLONE customers;
```

#### Q-2 Load data using COPY ? 

```console
COPY INTO customers FROM @stage;
```

#### Q-3 How to flatten JSON ?

```console
SELECT value FROM table, LATERAL FLATTEN(input => column);
```

#### Q-4 Performance Optimization ? Query on a 2TB table is slow.

```console
Add clustering key
Avoid SELECT *
Use filters on partitioned columns
Resize warehouse
Use result cache

ALTER TABLE sales CLUSTER BY (order_date);

```

#### Q-5 Cost Control?  Warehouse running continuously ?

```console
ALTER WAREHOUSE compute_wh
SET AUTO_SUSPEND = 60
AUTO_RESUME = TRUE;

```

#### Q-6 Difference between result cache, warehouse cache, and metadata cache? 

```console
| Cache Type      | Description                         |
| --------------- | ----------------------------------- |
| Result Cache    | Stores final query results (24 hrs) |
| Warehouse Cache | Local cache per warehouse           |
| Metadata Cache  | Used for query optimization         |


```

#### Q-7 COPY vs Snowpipe ? 

```console
| COPY           | Snowpipe               |
| -------------- | ---------------------- |
| Manual / batch | Continuous auto-ingest |
| User triggered | Event driven           |
| Cheaper        | Near real-time         |


```

#### Q-8 Difference between Time Travel and Fail-safe ?

```console
| Feature     | Time Travel             | Fail-safe           |
| ----------- | ----------------------- | ------------------- |
| User Access | Yes                     | No (Snowflake only) |
| Retention   | 1–90 days               | Fixed 7 days        |
| Purpose     | Query/restore past data | Disaster recovery   |
| Cost        | Configurable            | Included            |

Time Travel → Recover accidental delete
Fail-safe → Catastrophic failure recovery

```

#### Q-9 How Snowflake handles skewed data ?

```console
Snowflake mitigates skew using:
Automatic micro-partitioning
Dynamic query optimization
Distributed compute processing

Example

If one region has 90% of data:

Snowflake spreads processing across nodes
Uses adaptive execution to rebalance workloads
```

#### Q-10 When would you use a clustering key?

```console
Use a clustering key when:
Table is very large (TBs)
Queries frequently filter on the same column
Micro-partition overlap is high

ALTER TABLE sales CLUSTER BY (order_date);

```

#### Q-11 How multi-cluster warehouses improve concurrency ? 

```console
A multi-cluster warehouse automatically starts additional compute clusters when concurrency increases.

Example -
100 users run queries at the same time
Single cluster → queries queue
Multi-cluster → Snowflake spins up new clusters

```

#### Q-12

```console
```

#### Q-13

```console
```

#### Q-14

```console
```
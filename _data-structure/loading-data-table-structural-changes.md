---
title: Table Structural Changes
permalink: /data-structure/table-structural-changes
tags: [redshift_destination, panoply_destination, postgresql_destination, bigquery_destination]
keywords: redshift, amazon redshift, postgresql, varchar, varchar widening, column splitting, postgres, panoply, bigquery, structure change, schema change, column split

summary: "From time to time, Stitch will encounter data that can't be loaded losslessly into the destination table in your data warehouse. When this happens, Stitch may have to alter the structure of the table in order to successfully load the data."
toc: true
weight: 3
---

{{ page.summary }}

This can happen for a few reasons:

- Columns have been added to or removed from the table, 
- Columns have been removed from the table, or
- Multiple data types exist in a single column

In this guide, you'll find examples of how each destination handles each of these scenarios.

---

## Adding & Removing Columns

{% include note.html content="This section applies to **all data warehouses.**" %}

- **If a new column is added to the source table,** that column will be appended to the end of the table in the data warehouse.
- **If a column is removed from the source table,** default `NULLs` will be placed into the column going forward. Stitch does not remove columns from the data warehouse.

---

## Widening VARCHAR Columns

Depending on the data warehouse you're using, `VARCHAR` columns of varying sizes can result in Stitch taking different actions to accommodate the data.


{% include replication/templates/destination-tabs.html content="varchar-widening" %}

---

## Columns with Mixed Data Types {#columns-mixed-data-types}

Stitch requires that there only be one data type per column to properly type and store your data. If a column contains multiple data types, Stitch will create additional columns and append the data type to the column name. **The end result will vary slightly from destination to destination** - the result for each destination can be found after the example.

Let's take a look at an example using an `orders` table in an integration called `rep_sales`. During the structure sync, Stitch will create a schema called `rep_sales` in your data warehouse and inside this schema, a table called `orders`.

Excluding the `_sdc` columns, Stitch determines this is the table's structure:

{% highlight markdown %}
| Column           | Data Type    |
|------------------+--------------|
| id [pk]          | BIGINT       |
| order_amount     | BIGINT       |
| order_confirmed  | BOOLEAN      |
{% endhighlight %}

During the **first** sync, the following rows are replicated:

{% highlight markdown %}
| id [pk] | order_amount | order_confirmed |
|---------+--------------+-----------------|
| 1       | 12           |                 |
| 2       | 10           | true            |
{% endhighlight %}

During the **next** sync, the following rows are replicated:

{% highlight markdown %}
| id [pk] | order_amount | order_confirmed |
|---------+--------------+-----------------|
| 3       | 13.25        | true            |
| 4       | 11           | yes             |
{% endhighlight %}

Stitch will detect that the data types in these newly replicated rows differ than the ones from the initial sync. In this case:

- `order_amount` was originally a `BIGINT`, but can sometimes be a decimal
- `order_confirmed` was originally a `BOOLEAN`, but can sometimes be a string

To accommodate the data, Stitch will create a new column for the newly detected data type and append the data type to the column name.

**How columns are named as a result of "splitting" mixed data types depends on the type of destination you're using**. In the tabs below, you'll see what the structure of the `orders` table would be altered to for each destination type.

{% include replication/templates/destination-tabs.html content="mixed-data-types" %}

---

## Redshift/Panoply Dependent Views {#redshift-panoply-dependent-views}

{% include destinations/redshift/redshift-dependent-views.html %}

---

{% include data-structure/identifying-record-rejections.html %}
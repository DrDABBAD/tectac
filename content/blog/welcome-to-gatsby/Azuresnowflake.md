---
title: 'SNOWFLAKE ON AZURE'
date: 2021-04-06 13:32:20 +0300
description: Notes Azure with snowflake. # Add post description (optional)
img:  ./software.jpg# Add image post (optional)
---


## SNOWFLAKE ON AZURE: USING SNOWFLAKE THROUGH THE WEB UI

Typical services sued with Azure and snowflake

* Snowflake on Azure: Connect via web UI to manage your Snowflake account, provision warehouses, explore your Snowflake databases, run queries, etc.
* Azure Blob Storage: this stages the load files from any processing system.
* Azure Data Lake Store: usage clickstream logs storage
* PowerBI: used to visualize the results of the analytics

### WEB UI

Snowflake worksheet provides the object explorer on the left, the query editor in the center and the query results at the bottom. Looks like SMSS.

### Azure blob storage

Details on loading data from blob storage held here:

 [Azure Storage](https://www.snowflake.com/global-snowflake-loading-data-into-snowflake-from-azure-blob-storage/).

#### load data from Azure Blob Storage container to Snowflake


1. Creating a snowflake object reference

```snowflake
CREATE STAGE azstage
URL = azure://<storageaccount>.blob.core.windows.net/tpch1000
CREDENTIALS=(AZURE_SAS_TOKEN=…)
```

## Resource

[Azure and snowflake](https://www.snowflake.com/blog/how-to-get-started-with-snowflake-on-azure/)
# allow_quoted_newlines option at External Table on BigQuery

When you create an external table from CSV file on BigQuery, better check if any option is missing.

I noticed, one day that query by the external table got failed since original CSV file contains a quoted newline character at one of the fields.

For those case, you should use `allow_quoted_newlines` option for avoiding such error. 

The following is an example of the query using `allow_quoted_newlines` option.


```sql
CREATE OR REPLACE EXTERNAL TABLE example_dataset.example_table (
  id INT64,
  name STRING,
) OPTIONS (
   format = 'CSV'
  ,uris = ['gs://example_bucket/example.csv']
  ,skip_leading_rows = 1
  ,allow_quoted_newlines = True
);
```

# Reference

https://cloud.google.com/bigquery/docs/loading-data-cloud-storage-csv?hl=ja

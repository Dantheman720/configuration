# Query: Webpage Missing Data

**Webpage Missing Data** is a query that returns list of webpage documents
missing important data. Important data is: `sys_title`, `sys_description` or
`sys_content_plaintext`.

It also returns aggregation statistics about total count of missing docs per
individual fields.

The query requires **content provider authentication** and allows only `rht`
or `jboss-developer` providers (or admin). Based on the provider it operates
on top of relevant data set.

## URL parameters

No URL parameters accepted.

**Example:**

- <http://dcp_server:port/v2/rest/search/webpage_missing_data>

## Query output format

Up to 50 first matching documents are returned in `hits.hits[]`. Every returned document contains
important fields (see above for the list) and `check#` fields with missing flag. This way it is easy
to learn which particular fields were missing for individual documents.

Section `aggregations.sys_content_type` contain document total count broken down by `sys_content_type`.
And each subsection contains `missing#` sub-aggregation with total number of missing documents per important field.

## Query implementation details

Source of the query can be found in [`webpage_missing_data.json`](webpage_missing_data.json) file.
It is not string-encoded ATM thus the source is perfectly readable.
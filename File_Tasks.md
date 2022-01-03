# `File_Tasks` Endpoint
URL: `https://www.drivethrurpg.com/api/v1/file_tasks`
Method: `POST`

Get info for a specific file, including download URL.

## Authorization
Pass [[Token]] in Header:
`"Authorization: Bearer <token>"`

## Passable Options
* `fields` ([[#Fields|options]])

## `POST` Data
Info to pass comes from [[Products]] data. 

Field | Description
------|-------------
`products_id` | Product ID, numeric
`bundle_id` | Number of file, if multiple files in product. Numeric

Both `product_id` and `bundle_id` are required or the request will be rejected. Must be sent as form fields (not JSON).

Example: `"products_id=381334&bundle_id=1"`

## Return Data

### Fields
Field | Description
------|-------------
`download_url` | URL for file download
`file_tasks_id` | Interal identifier for file request
`progress` | Returns `"Preparing download..."` while watermarking file, `"Complete"` when ready to download
`checksums` |Two subfields: `checksum` and `checksum_date`. Self-explanatory.
`last_modified` | Last modification timestamp

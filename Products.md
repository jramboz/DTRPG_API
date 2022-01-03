# `Products` Endpoint
URL: `https://www.drivethrurpg.com/api/v1/customers/<customer_id>/products`
Method: `GET`

Get list of products in customer account.

## Authorization
Pass [[Token]] in Header:
`"Authorization: Bearer <token>"`

## Passable Options
* `fields` ([[#Fields|options]]) - Product info fields to retrieve
* `embed` ([[#Embed|options]]) - Extra info to embed?
* `page` - Result pagination number
* `per_page` - Results per page (500 max?)
* `include_archived` - Should results include archived files? `0` or `1`

## Return Data
Returns an array of objects. Each object has fields and/or embeds

### Fields
Field | Description
------|-------------
`products_id` | Product ID. Seems to be global.
`products_name` | Product name
`is_archived` | Archived or not. `0` or `1`
`cover_url` | URL of cover thumbnail. 140px? Escaped.
`cover_url_fullsize` | URL of full-sized cover. Escaped.
`products_thumbnail100` | URL of product thumbnail. 100px? Escaped.
`date_purchased` | Date of purchase. Example: `2019-01-15T13:35:08-05:00`
`products_filesize` | Product filesize. For all files combined? Number as string - MB?
`publishers_name` | Publisher name. Special characters replaced with html codes.

### Embed
Can specifty two families of embedded options, `files` and `filters`. Each will include a sub-object in the product object.

**Note to self:** Maybe these are shortcuts to other endpoints? -- Nope, at least not obvious ones.

#### Files Fields
Field | Description
------|-------------
`files.bundle_id` | Sequential number of file within product. 0-indexed.
`files.filename` | Filename
`files.last_modified` | Timestamp for last file modification
`files.checksums` | Two subfields: `checksum` and `checksum_date`. Self-explanatory.
`files.raw_filesize_bytes` | Number: filesize in bytes

#### Filters Fields
Field | Description
------|-------------
`filters.filters_name` | Name of filter
`filters.filters_id` | Number as string, filter ID 
`filters.parent_id` | If this is a sub-filter, `filters_id` of parent. Otherwise `0`
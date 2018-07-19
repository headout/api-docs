# Category/Collection Models

A category (also called collection) is a higher level grouping for products. There can be several products in a category and a product can be there in multiple categories. Also every product has exactly 1 primary category.

* [`category`](#category)

### `category`

The category super object.

KEY | TYPE | NULL/EMPTY | DESCRIPTION
--- | --- | --- | ---
id | string | no | The ID of the category.
name | string | no | The display name of the category.
cityCode | string | no | The city of the category. Eg: `NEW_YORK`, `DUBAI`
canonicalUrl | string | no | The canonical url for the category page on `www.headout.com`. If a separate category page is being constructed for this category then you are required to add this url as canonical url in the HTML code using `<link rel="canonical">`. This url can also be used to open the concerned category page on `www.headout.com`.

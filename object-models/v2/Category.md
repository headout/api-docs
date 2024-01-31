### `Category`

Represents a primary category associated with a product.

| KEY                | TYPE                  | NULL/EMPTY | DESCRIPTION                                                                                                |
|--------------------|-----------------------|------------|------------------------------------------------------------------------------------------------------------|
| id                 | String                | no         | Unique identifier for the category.                                                                        |
| name               | String                | no         | Name of the category.                                                                                      |
| localeSpecificUrls | Map<Language, String> | no         | Mapping of languages to their respective URL strings for the category. This map can be empty but not null. |
| canonicalUrl       | String                | no         | Complete URL of the category, based on the English language URL slug.                                      |

The `Category` class categorizes products into primary categories. Each category has a unique `id` and a `name`. The `localeSpecificUrls` are mappings of language codes to URL strings, providing language-specific access to the category. The `canonicalUrl` is a permanent web address derived from the English URL slug.
### `SubCategory`

Represents a subcategory within a product's categorization system.

| KEY                | TYPE                  | NULL/EMPTY | DESCRIPTION                                                             |
|--------------------|-----------------------|------------|-------------------------------------------------------------------------|
| id                 | String                | no         | Unique identifier for the subcategory.                                  |
| name               | String                | no         | Name of the subcategory.                                                |
| categoryId         | String                | no         | Identifier of the parent category to which this subcategory belongs.    |
| canonicalUrl       | String                | no         | Canonical URL of the subcategory. It can be null.                       |
| localeSpecificUrls | Map<Language, String> | no         | Mapping of languages to their respective URL slugs for the subcategory. |

This data class `SubCategory` is utilized to provide detailed information about a specific subcategory related to a product. Each subcategory is uniquely identified by its `id`, and is described with a `name`. The `categoryId` links the subcategory to its parent category. The `canonicalUrl` provides a permanent URL for online resources, and the `urlSlugs` offers language-specific endpoints for accessing subcategory-related information.
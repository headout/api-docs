### `Category`

Represents a primary category associated with a product.

| KEY          | TYPE                  | NULL/EMPTY | DESCRIPTION                                                          |
|--------------|-----------------------|------------|----------------------------------------------------------------------|
| id           | String                | no         | Unique identifier for the category.                                  |
| name         | String                | no         | Name of the category.                                                |
| urlSlugs     | Map<Language, String> | no         | Mapping of languages to their respective URL slugs for the category. |
| canonicalUrl | String                | no         | Canonical URL of the category. It can be null.                       |

The `Category` data class is designed to categorize products into primary categories. Each category is identified by a unique `id` and a descriptive `name`. The `urlSlugs` provide language-specific URLs for the category, enhancing accessibility for users in different linguistic regions. The `canonicalUrl` gives a permanent web address for the category.
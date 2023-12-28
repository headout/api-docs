### `Collection`

Represents a collection of products or experiences grouped together, often related by theme or location.

| KEY          | TYPE                  | NULL/EMPTY | DESCRIPTION                                                            |
|--------------|-----------------------|------------|------------------------------------------------------------------------|
| id           | String                | no         | Unique identifier for the collection.                                  |
| name         | String                | no         | Name of the collection.                                                |
| city         | String                | no         | Name of the city associated with the collection.                       |
| urlSlugs     | Map<Language, String> | no         | Mapping of languages to their respective URL slugs for the collection. |
| canonicalUrl | String?               | yes        | Canonical URL of the collection. It can be null.                       |

The `Collection` data class is used to aggregate products or experiences into meaningful groups or collections. Each collection is uniquely identified by an `id` and is named with a `name` that reflects its theme or focus. The `city` field indicates the city where the collection is primarily relevant or located. The `urlSlugs` provide language-specific URLs for the collection, facilitating user access across different regions. The `canonicalUrl` serves as a permanent web address for the collection.
# API naming scheme

The API naming is structured into 4 components. Resource, view, action and filter.

#### Resource

###### API sub structure

`/<resource>`

###### Definition

Resource specifies a particular model which has it's own identity. Typically a resource will always have a `id` and it will make sense to refer these resources by their IDs and do operations over them.

###### Usage

The resource is the first part of the API structure (excluding the versioning).

###### Example
`/product/get/{id}`: Refers to the `product` resource identified by the [`product`](/object-models/product-models.md#product) which is being fetched by it's ID.

#### View

###### API sub structure

`/<resource>/<view>`

###### Definition

A view specifies a distinct view of the resource. Typically, views will not have their own identifiers and the object pivot will still be at a resource level. Views can have information both present or not present in the main resource object, nevertheless, all the information is linked to the resource in question. The identification of view still happens using the resource.

###### Usage

A view can occur **only** after a resource.

###### Example

`/product/listing/list-by/city`: Fetches a list of `listing` view ([`product-listing`](/object-models/product-models..md#product-listing)) for the `product` resource filtered by city.

#### Action

###### API sub structure

`/<resource>/<action>`

`/<resource>/<view>/<action>`

###### Definition

An action defines the verb which needs to be performed on the resource or on it's view. Each action has a specific functionality.

* `get`: Used to fetch the resource or it's view using the ID of the resource. It is mandatory to have `{id}` **immediately after** this action.
* `list`: Used to fetch a list of the resource or it's view using multiple IDs of the resource. It is mandatory to have `ids` as a **query param** for this action.
* `list-by`: Used to fetch a list of the resource or it's view which is filtered by the subsequent filter. The filer criteria is always input in the query params. *Ref: [Filter](#Filter)*
* `create`: Used to create a resource.

###### Usage

An action can occur **only** after either a resource or it's view.

###### Example

`/product/get/{id}`: Fetch the [`product`](/object-models/product-models.md#product) resource identified by it's ID.

`/product/listing/list`: Fetches a list of `listing` view ([`product-listing`](/object-models/product-models..md#product-listing)) for the `product` identified by the `product` IDs. This will have a query param `ids`.

`/inventory/list-by/variant`: Fetches a list of [`inventory`](/object-models/inventory-pricing-models.md#inventory)) resource filtered by variant. This will have a query param of `variantId`.

`/booking/create`: Used to create a booking.

#### Filter

###### API sub structure

`/<resource>/list-by/<filter>`

`/<resource>/<view>/list-by/<filter>`

###### Definition

A filter is a special path param for `list-by` action. It is supposed to denote a filter criteria which will be used to list either the resource or it's view. The actual filter criteria input happens in the query params.

###### Usage

Filter can only be used after a `list-by` action.

###### Example

`/product/listing/list-by/city`: Fetches a list of `listing` view ([`product-listing`](/object-models/product-models..md#product-listing)) for the `product` resource filtered by `city`. The filter criteria input will happen using the `cityCode` query param.

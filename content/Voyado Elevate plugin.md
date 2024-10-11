
# APIs

Elevate has two APIs, storefront and admin

## Elevate admin API

### Import

https://docs.apptus.com/elevate/4/guides/import-export-pages/?h=page+import#minimal-examples

Endpoint `/admin/v3/import/data` can import all the data, products, groups, and content at the same time. They say full import should be used hourly if the store has less than 10000 entries. 

There’s a possibility to send a gzipped file, so it might be a good idea to implement something like https://github.com/maennchen/ZipStream-PHP 

- Products importer
- Variant importer
- Product groups importer ([depends on where they want to edit them](https://www.notion.so/Voyado-Elevate-plugin-d41165eb668246b8a3661fed697b273b?pvs=21))

### Export

Instead of using API, navigation can be exported from Voyado to product categories depending on where they prefer editing it by using `/admin/v3/export/navigation` endpoint

 

## Elevate storefront API

### Autocomplete

https://docs.apptus.com/elevate/4/integration/api/specifications/storefront/v3/queries/autocomplete/

### Recommendations

- Add to cart: https://docs.apptus.com/elevate/4/integration/api/specifications/storefront/v3/queries/add-to-cart-popup/
- Cart page: https://docs.apptus.com/elevate/4/integration/api/specifications/storefront/v3/queries/cart-page/
- Product page: https://docs.apptus.com/elevate/4/integration/api/specifications/storefront/v3/queries/product-page/

### Search

https://docs.apptus.com/elevate/4/integration/api/specifications/storefront/v3/queries/search-page/

# Live search

## Short-code

Live search short-code should provide a rendering of the search box with an integrated [[#Autocomplete]] and [[#Search]] API functionality. 

### Search results

Possibility to create a page separate from wordpress/woocommerce search results as it might take a huge amount of time to try to hook the WP_Query to support custom filters, ordering etc.

# Recommendations

## Short-code(s)

Can be implemented as a single short-code with `recommendation type` as a parameter. Possibly `presentation` as the second parameter (small list, big list, etc.)

- `ADD_TO_CART_RECS`	Add-to-cart popup
- `ALTERNATIVES`	Product details page
- `CART`	Cart/Checkout page
- `FAVORITES`	Homepage or Landing page
- `MORE_FROM_SERIES`	Product details page
- `NEWEST_PRODUCTS`	Homepage or a Landing page (likely dedicated to new arrivals)
- `PERSONAL`	Homepage or Landing page
- `RECENTLY_VIEWED`	Product details page or Landing page
- `STYLE_WITH`	Product details page
- `TOP_PRODUCTS`	Homepage
- `UPSELL`	Product details page

# Customers key / session key

### Customers key

Customer key can be generated and stored in session for non-logged-in customers, meta for logged-in ones

If a customer decides to create an account, the session customer key can be stored as meta.

### Session key

Short-lived session identifier for the customer. https://docs.apptus.com/elevate/4/integration/behavioral-data/visitor-identification/?h=session#selecting-visitor-identifier

# Event handling

We can use they JS library to utilise event tracking for the customer: https://docs.apptus.com/elevate/4/integration/api/javascript-library/

CustomerKey, SessionKey, etc. have to be available for JS to consume

|                             | Min | Max |
| --------------------------- | --- | --- |
| Admin settings              | 2   | 3   |
| Elevate admin API           |     |     |
| Import                      | 6   | 8   |
| Export                      | 4   | 5   |
| Elevate storefront API      |     |     |
| Autocomplete                | 1   | 2   |
| Recommendations             | 1   | 2   |
| Live search                 |     |     |
| Shortcode                   | 15  | 20  |
| Search results              | 20  | 25  |
| Recommendations             |     |     |
| Shortcode(s)                | 4   | 5   |
| Customers key / session key |     |     |
| Customers key               | 2   | 3   |
| Session key                 | 1   | 2   |
| Event handling              | 3   | 4   |
|                             | 65  | 80  |
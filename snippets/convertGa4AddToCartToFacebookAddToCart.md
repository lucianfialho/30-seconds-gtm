The snippet converts Google Analytics 4 (GA4) `add_to_cart` event data to `AddToCart` event data for Facebook Pixel format.

> You have must be created `{{ecommerce}}` dataLayer variable on Google Tag Manager copy code below.

- Collect and prepare data: Extract relevant information from the GA4 event, such as product IDs, names, quantities, and prices.
- Map to Facebook Pixel format: Use JavaScript to transform the GA4 data into the format required by the Facebook Pixel AddToCart event.
- Used JavaScript methods:
  - .map(): Convert the array of items from GA4 into an array suitable for the Pixel, detailing each product's ID, name, quantity, and price.
  - Other operations might include filtering or reducing data, depending on the complexity of the transformation required.

```js
function () {
  return {
    content_ids: {ecommerce}.items.map(item => item.item_id),
    content_type: 'product',
    contents: {ecommerce}.items.map(item => ({
      id: item.item_id,
      quantity: item.quantity,
      item_price: item.price,
    })),
    currency: {ecommerce}.currency,
    value: {ecommerce}.value,
  };
}
```

```js
// output: {content_name: "Stan and Friends Tee", content_category: "Apparel", content_type: "product", content_ids: ["SKU_12345"], contents: [{id: "SKU_12345", quantity: 1, item_price: 9.99}], currency: "USD", value: 7.77}
```

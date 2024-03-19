The snippet converts Google Analytics 4 (GA4) `view_item` event data to `viewContent` event data for Facebook Pixel format.

> You have must be created `{{ecommerce}}` dataLayer variable on Google Tag Manager copy code below.

- Uses .map() to transform each item into a Facebook Pixel-compatible object.
- Extracts and maps information such as product name, category, ID, and price.
- This conversion facilitates integrated analysis between GA4 and Facebook Pixel.

```js
function () {
  return {
    content_name: {{ecommerce}}.items[0].item_name,
    content_category: {{ecommerce}}.items[0].item_category,
    content_type: "product",
    content_ids: [{{ecommerce}}.items[0].item_id],
    contents: {{ecommerce}}.items.map((item) => ({
      id: item.item_id,
      quantity: item.quantity,
      item_price: item.price,
    })),
    currency: {{ecommerce}}.currency,
    value: {{ecommerce}}.value,
  };
}
```

```js
// output: {content_name: "Stan and Friends Tee", content_category: "Apparel", content_type: "product", content_ids: ["SKU_12345"], contents: [{id: "SKU_12345", quantity: 1, item_price: 9.99}], currency: "USD", value: 7.77}
```

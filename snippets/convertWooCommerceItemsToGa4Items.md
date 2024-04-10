Convert a list of items from a `WooCommerce` event into the recommended format for `Google Analytics 4 (GA4)` using a custom JavaScript function in `Google Tag Manager`. The provided code snippet processes the `items` array, which originates from an `ecommerce` event, mapping each item to a new format that aligns with `GA4's e-commerce data model` requirements. This transformation ensures compatibility with `GA4's enhanced e-commerce` tracking features.

> You have must be created `{{ecommerce}}` dataLayer variable on Google Tag Manager.

- Return `items` list with a recomended GA4 pattern.  

* Remember to check if the event parameters match the structure we prepared. Parameters may change due to WooCommerce updates.

```js
function() {
  return {{ecommerce}}.items.map(function(item) {
    return {
      item_id: item.item_id.toString(),
      price: parseFloat(item.price),
      quantity: parseInt(item.quantity) || 1,
      item_name: item.item_name,
      item_variant: item.item_variant || item.variant,
      item_category: item.item_category
    };
  });
}
```

```js
// output: 
[
  {
    "item_id": "001",
    "price": "19.99",
    "quantity": "2",
    "item_name": "Graphic Tee",
    "item_variant": "Medium",
    "item_category": "T-shirts"
  },
  {
    "item_id": "002",
    "price": "29.99",
    "quantity": "1",
    "item_name": "Hoodie",
    "item_variant": "Large",
    "item_category": "Outerwear"
  }
]
```
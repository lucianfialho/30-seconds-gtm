Convert a list of products from the Vtex `orderPlaced` event into the format recommended for Google Analytics 4 (GA4) using a custom JavaScript function in Google Tag Manager. In Vtex, the `orderPlaced` event is utilized instead of `purchase`. The provided code snippet facilitates the conversion of the `orderPlaced` event model to the `purchase` model recommended by GA4. It processes the products array within the ecommerce object, which is part of the `orderPlaced` event in Vtex. The function maps each product to a new format that aligns with GA4's e-commerce data model requirements, ensuring compatibility with GA4's enhanced e-commerce tracking features.

> You must create the variable `{{ecommerceV2}}` in Google Tag Manager to capture the object containing transaction data in the `orderPlaced` event.

- Return `items` list with a recomended GA4 pattern.  

* Remember to check if the event parameters match the structure we prepared. Parameters may change over time.

```js
function () {
  return {{ecommerceV2}}.ecommerce.purchase.products.map(function(item){
    return {
      'item_id': item.id.toString(),
      'item_name': item.name,
      'currency': item.currency || 'BRL',
      'item_brand': item.brand,
      'item_category': item.item_category || item.category,
      'price': parseFloat(item.price),
      'quantity': parseInt(item.quantity) || 1
    }
  })
}
```

```js
// output:
[
  {
    "item_id": "101",
    "item_name": "Sneakers",
    "currency": "USD",
    "item_brand": "BrandA",
    "item_category": "Footwear",
    "price": 59.99,
    "quantity": 1
  }
]
```
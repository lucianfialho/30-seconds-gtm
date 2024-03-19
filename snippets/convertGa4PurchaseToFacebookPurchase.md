The snippet converts Google Analytics 4 (GA4) `purchase` event data to `Purchase` event data for Facebook Pixel format.

> You have must be created `{{ecommerce}}` dataLayer variable on Google Tag Manager copy code below.

- Collect and prepare data: Extract relevant information from the GA4 event, such as product IDs, names, quantities, and prices.
- Map to Facebook Pixel format: Use JavaScript to transform the GA4 data into the format required by the Facebook Pixel Purchase event.
- Used JavaScript methods:
  - .map(): Convert the array of items from GA4 into an array suitable for the Pixel, detailing each product's ID, name, quantity, and price.
  - Other operations might include filtering or reducing data, depending on the complexity of the transformation required.

```js
function () {
  return {
    content_ids: {{ecommerce}}.items.map(item => item.item_id),
    content_type: 'product',
    contents: {{ecommerce}}.items.map(item => ({
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
// output:
{
  "content_ids": ["T123", "C456"],
  "content_type": "product",
  "contents": [
    {
      "id": "T123",
      "quantity": 1,
      "item_price": 20.00
    },
    {
      "id": "C456",
      "quantity": 1,
      "item_price": 10.00
    }
  ],
  "currency": "USD",
  "value": 30.00
}
```

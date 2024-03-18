Convert a Google Analytics `items` or `ecommerce.items` in `contents` param to Facebook Pixel data, see the documentation [guide](https://developers.facebook.com/docs/meta-pixel/reference/#object-properties). You have must be created `{{ecommerce}}` dataLayer variable on Google Tag Manager copy code below.

> You have must be created `{{ecommerce}}` dataLayer variable on Google Tag Manager copy code below.

- Return a ecommerce object with Facebook `contents` pattern
- Use `Array.prototype.map()` to return a array of objects;

```javascript
    function() {
        return {{ecommerce}}.items.map(product => ({
            id: product.item_id,
            quantity: product.quantity
        }));

    }
```

```js
/* output: 
[{
    id: '12345',
    quantity: 1
}]

*/
```

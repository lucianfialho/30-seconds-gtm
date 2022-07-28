Convert a Google Analytics Enhanced Commerce click action to Google Analytics 4 `remove_from_cart` event object, see the Google Tag Manager [guide](https://developers.google.com/tag-manager/enhanced-ecommerce?hl=pt_br#cart). You have must be created `{{ecommerce}}` dataLayer variable on Google Tag Manager copy code below.

> You have must be created `{{ecommerce}}` dataLayer variable on Google Tag Manager copy code below.

- Return a ecommerce object with GA4 pattern
- Create a items key
- Use `Array.prototype.map()` to return a array of objects;

```javascript
    function() {
        return {
            ecommerce: {
                items: {{ecommerce}}.remove.products.map(function(product){
                    return {
                        item_name: product.name,    
                        item_id: product.id,
                        price: product.price,
                        item_brand: product.brand,
                        item_category: product.category,
                        item_variant: product.variant,
                        quantity: product.quantity
                    }
                })
            }
        }
    }
```
```js
/* output: 
{
    ecommerce: {
        items: [{
            item_name: 'Triblend Android T-Shirt',    
            item_id: '12345',
            price: '15.25',
            item_brand: 'Google',
            item_category: 'Apparel',
            item_variant: 'Gray',
            quantity: 1
        }]
    }
}
*/
```

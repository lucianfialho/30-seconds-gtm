Convert a Google Analytics Enhanced Commerce click action to Google Analytics 4 select_item event object.

```html
    <script>
        // See more: https://developers.google.com/tag-manager/enhanced-ecommerce?hl=pt_br#cart
        dataLayer.push({
            'event': 'removeFromCart',
            'ecommerce': {
                'currencyCode': 'EUR',
                'remove': {
                    'products': [{
                        'name': 'Triblend Android T-Shirt',
                        'id': '12345',
                        'price': '15.25',
                        'brand': 'Google',
                        'category': 'Apparel',
                        'variant': 'Gray',
                        'quantity': 1
                    }]
                }
            }
        });
    </script>
```

You have must be created `{{ecommerce}}` dataLayer variable on Google Tag Manager.

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
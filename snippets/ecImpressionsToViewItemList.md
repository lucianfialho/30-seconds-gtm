Convert a Google Analytics Enhanced Commerce impressions action to Google Analytics 4 view_item_list event object.

```html
    <script>
        // See more in: https://developers.google.com/tag-manager/enhanced-ecommerce?hl=pt_br#product-impressions
        dataLayer.push({
            'ecommerce': {
                'currencyCode': 'EUR',
                'impressions': [{
                    'name': 'Triblend Android T-Shirt',
                    'id': '12345',
                    'price': '15.25',
                    'brand': 'Google',
                    'category': 'Apparel',
                    'variant': 'Gray',
                    'list': 'Search Results',
                    'position': 1
                }]
            }
        });
    </script>
```


You have must be created `{{ecommerce}}` dataLayer variable on Google Tag Manager copy code below.

```javascript
    function() {
        return {
            ecommerce: {
                items: {{ecommerce}}.impressions.map(function(product){
                    return {
                        item_name: product.name,    
                        item_id: product.id,
                        price: product.price,
                        item_brand: product.brand,
                        item_category: product.category,
                        item_variant: product.variant,
                        item_list_name: product.list,
                        item_list_id: product.list,
                        index: product.position,
                        quantity: product.quantity
                    }
                })
            }
        }
    }
```
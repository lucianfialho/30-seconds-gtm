Convert a Google Analytics Enhanced Commerce click action to Google Analytics 4 select_item event object.

```html
    <script>
        // See more: https://developers.google.com/tag-manager/enhanced-ecommerce?hl=pt_br#product-clicks
        dataLayer.push({
            'event': 'productClick',
            'ecommerce': {
                'click': {
                    'actionField': {'list': 'Search Results'},
                    'products': [{
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
            }
        })
    </script>
```

You have must be created `{{ecommerce}}` dataLayer variable on Google Tag Manager.

```javascript
    function() {
    return {
        ecommerce: {
            items: {{ecommerce}}.click.products.map(function(product){
                return {
                    item_name: product.name,    
                    item_id: product.id,
                    price: product.price,
                    item_brand: product.brand,
                    item_category: product.category,
                    item_variant: product.variant,
                    item_list_name: {{ecommerce}}.click.actionField.list,
                    index: product.position,
                    quantity: product.quantity
                }
            })
        }
    }
  }
```
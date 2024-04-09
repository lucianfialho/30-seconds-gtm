Captures and converts the data from a submitted form into a javascript object

> Before using this code, you must have created a `{{Form Element}}` built-in variable in Google Tag Manager that captures the form element involved in the submit event.

- `if({{Event}} === 'gtm.formSubmit')` checks if `gtm.formSubmit` event;
- `var formElement = {{Form Element}}` Collects form data: Iterates through all form elements, excluding submit buttons, to collect their names and values.
- `for` interates over all form elements to collect their data
- `if` checks if an element has name and is not a submit button before including it in the data object
- `formData[element.name]` JSON object creation: Constructs a JSON object with name-value pairs for each form field, preparing the data for use in tags or variables.
- `return formData` return javascript object

```js
function() {

  var formData = {};
  if ({{Event}} === 'gtm.formSubmit') {
    var formElement = {{Form Element}}
    var elements = formElement.elements;
    for (var i = 0; i < elements.length; i++) {
      var element = elements[i];
      if (element.name && element.type !== 'submit') {
        formData[element.name] = element.value;
      }
    }
  }

  return formData;
}
```

```js
// output:
{
  first_name: "Maria",
  last_name: "Joana",
  email: "mj@metricasboss.com.br",
  remember: true
}
```

--- DEPRECATED Google Analytics Universal Analytics are not colleting information since july 2023
Create a Google Analytics object with trackingId: clientId (key:value).

- Prevent error using `try...catch` statement
- Get global Google Analytics instances `ga.getAll()`;
- Use `Array.prototype.reduce()` to convert array of objects with in object with `{trackingId: clientId}` format;

```javascript
function() {
  try {
    var trackers = ga.getAll();
    return trackers.reduce(function(accumulator, tracker){
      accumulator[tracker.get('trackingId').replace(/-/g, '_')] = tracker.get('clientId')
      return accumulator
    }, {})
  } catch(e) {}
  return false;
}
```

```javascript
// output
{
  UA_60130206_1: "1768769809.1636989574";
}
```

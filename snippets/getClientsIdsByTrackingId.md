Create a Google Analytics object with trackingId: clientId (key:value).

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
    UA_60130206_1: '1768769809.1636989574'
}
```
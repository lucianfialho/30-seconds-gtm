Create a Google Analytics 4 object with trackingId: `client_id` and `session_id`.

- Prevent error using `try...catch` statement
- Get global `client_id` from `window.gaGlobal`;
- Get `session_id` from container cookie `ga_{container_id}` `Array.prototype.reduce()` to a array of objects with `{trackingId: clientId} format;

```javascript
function() {
  try {
    var cookieName = '_ga_XXXXXXXX'; // Add your container id

    var regex = new RegExp(`${cookieName}=GS(\\d)\\.(\\d)\\.(\\w+)\\.(\\d+)`);

    var match = document.cookie.match(regex);

    if (match) {
        var sessionId = match[3];
    }
    return {
      client_id: window.gaGlobal.vid,
      session_id: sessionId,
    };

  } catch(e) {}
  return false;
}
```

```javascript
// output
{
  client_id: "1768769809.1636989574";
  session_id: "1768761829";
}
```

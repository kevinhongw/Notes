# Local Storage vs Session Storage vs Cookie

## LocalStorage

- Stores data with no expiration date, and gets cleared only through JavaScript, or clearing the Browser cache / Locally Stored Data
- Storage limit is the maximum amongst the three

## SessionStorage

- The sessionStorage object stores data only for a session, meaning that the data is stored until the browser (or tab) is closed.
- Data is never transferred to the server. (At least not naturally, can still be done through JS)
- Storage limit is larger than a cookie (at least 5MB).

## Cookie

- Stores data that has to be sent back to the server with subsequent requests. Its expiration varies based on the type and the expiration duration can be set from either server-side or client-side (normally from server-side).
- Cookies are primarily for server-side reading (can also be read on client-side), localStorage and sessionStorage can only be read on client-side.
  - In other word, cookies automatically attached to headers if the same domain and path defined in the cookie match the request.
- Size must be less than 4KB.
- Cookies can be made secure by setting the httpOnly flag as true for that cookie. This prevents client-side access to that cookie

## Takeaway

- LocalStorage and SessionStorage is saved locally so can't be read by server, which eliminates the security issue that cookies present.
- Local storage data persist until user or web app manually clears the browser cache.
- Session storage data persist until window or tab is closed.

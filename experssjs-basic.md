# Node/Express note

## Routing

```js
(req, res) => {
  // return value
  res.send(...)
  res.json(...)
}
```

## MVC

route -> controller -> return

## Middleware

#### req

User signs in with `<form>` and `POST`s to `/login`

`-> next()`

#### bodyParser

body parser makes the data available on the req object
`req.body.email = " abc@gmail.com "`

`-> next()`

#### emailNormalize

an email middleware might prepare/validate data

```js
req.body.email = req.body.email.trim().toLowerCase();
req.body.email; // "abc@gmail.com"
```

`-> next()`

#### authorizeUser

auth middlewrae will lookup the user and check their password

#### display

- Valid
- Invalid

### Code

```js
exports.myMiddleware = (req, res, next) => {
  req.name = "Kevin";
  next();
};

// in router
router.get("/", myController.myMiddleware, myController.homePage);
```

### Error handling

So middleware execute in order.

```js
// we came here after ALL the middleware before it
app.use("/", routes);

// so when no routes is matched, we need to catch it
app.use(errorHandlers.notFound);
```

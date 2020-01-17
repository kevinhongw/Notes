# Cypress notes

- The `.should()` command allows us to pass a callback function that takes the yielded subject as its first argument. This works just like .then(), except Cypress automatically waits and retries for everything inside of the callback function to pass.
- Modify timeout:

```js
// we've modified the timeout which affects default + added assertions
cy.get(".mobile-nav", { timeout: 10000 })
  .should("be.visible")
  .and("contain", "Home");
```

## Best practice

- When test /login, we don't want to test anything on `Home` page because we are testing the `login`
- `index.js` folder in `support` will always get run first (contain global config, custom command)
- **Don't** use the UI to build up state. Set state directly / programmatically
- **Don't** use page objects to share UI knowledge. Write specs in isolation, avoid coupling.
- **Don't** limit yourself trying to act like a user. You have native access to everything.

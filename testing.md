## Coverage

`yarn test:coverage`

that will create a `coverage` folder

then you have a `lcov-report` folder inside this one, open the `index.html` and you can explore

## Cypress

### Adjust Settings

in `cypress.config.js`

```jsx
baseUrl: 'http://localhost:3001',
```

in `environments.js`

```jsx
caseManager: {
      email: 'admin@localyzea.de',
      password: '12345678Aa!',
    },
```

### Running the tests

To run the cypress UI: `./node_modules/.bin/cypress open`

You can run the tests live in the browser by adding the `--head` or you can just enter the command

Alternatively, you can run the tests with `yarn cypress run`

Run and debug Single Cypress test

`yarn cypress run --spec cypress/e2e/variablesEditor/variablesEditor.spec.ts --no-exit -b chrome --headed`

Run and debug Single Cypress test

`yarn e2e —spec cypress/integration/talent/login.spec.ts --no-exit`

In order run the e2e tests, you have to seed the rails env with test data

`RAILS_ENV=test bin/rails db:seed`

sometimes you have to migrate and then run this command again

then run the rails env with test

`RAILS_ENV=test bin/rails s`

If it is still not working, try to build the FE with `yarn build`

Then you can run `yarn cypress open`

## Jest and Memory Leakage

You can use workerIdleMemoryLimit on jest config to limit the max of allocated memory (I used 512MB) to discover which test was stuck. And  yarn test --logHeapUsage  to check the memory consumption per test file.

## Redux Saga

- A yield can either be a blocking effect (`take`) or a non-blocking effect (`takeEvery`)

- `Put` is one example of what we call an Effect
  - example: `yield put({ type: 'INCREMENT' })`

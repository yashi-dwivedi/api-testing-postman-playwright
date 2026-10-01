# API Testing — Postman & Playwright (Restful Booker)

API test suite covering CRUD operations (Create, Read, Update, Delete) on the [Restful Booker](https://restful-booker.herokuapp.com/) public demo API, tested manually with **Postman** and automated with **Playwright + TypeScript**.

## What this project covers

- **Authentication:** generating an auth token (`POST /auth`)
- **Create:** creating a new booking (`POST /booking`)
- **Read:** retrieving a booking by ID (`GET /booking/{id}`)
- **Update:** updating a booking (`PUT /booking/{id}`)
- **Delete:** deleting a booking (`DELETE /booking/{id}`)

Each request/test includes assertions on status codes, response structure, and field values. Tests are chained so each step uses data from the previous one (auth token, booking ID), using Postman environment variables in the manual suite and TypeScript variables with `test.describe.serial` in the automated suite.

## Files

- `Restful Booker API Tests.postman_collection.json` — Postman collection
- `Restful Booker Env.postman_environment.json` — Postman environment
- `tests/booking-api.spec.ts` — Playwright + TypeScript automated API tests
- `playwright.config.ts` — Playwright configuration

## How to run

### Postman
1. Import both JSON files into Postman
2. Select "Restful Booker Env" as the active environment
3. Run requests in order: Create Auth Token → Create Booking → Get Booking → Update Booking → Delete Booking

### Playwright

npm install
npx playwright test
npx playwright show-report


## Known limitation

The `PUT /booking/{id}` (Update) endpoint on this public Heroku-hosted demo API returns inconsistent results (`200`, `403`, or `405`) across identical, correctly-formed requests, verified with valid Basic Auth, correct headers, and a valid body, in both Postman and Playwright. GET, POST, and DELETE operations are consistently reliable. The Playwright test for this endpoint logs the actual response status rather than asserting a fixed one, to avoid a flaky external dependency causing false failures. This points to instability on the server side of this free-tier demo API.

## Tech stack

- Postman (manual/exploratory testing with assertions)
- Playwright + TypeScript (automated API testing)

## Author

**Yashi Dwivedi**
QA Analyst transitioning into automation testing.
[GitHub](https://github.com/yashi-dwivedi)
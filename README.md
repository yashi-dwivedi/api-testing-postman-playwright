# API Testing — Postman & Playwright (Restful Booker)

API test suite covering CRUD operations (Create, Read, Update, Delete) on the [Restful Booker](https://restful-booker.herokuapp.com/) public demo API, built with **Postman** and (next) automated in **Playwright with TypeScript**.

## What this project covers

- **Authentication:** generating an auth token (`POST /auth`)
- **Create:** creating a new booking (`POST /booking`)
- **Read:** retrieving a booking by ID (`GET /booking/{id}`)
- **Update:** updating a booking (`PUT /booking/{id}`)
- **Delete:** deleting a booking (`DELETE /booking/{id}`)

Each request includes automated assertions (status codes, response structure, and field values), run through Postman's test scripts, with request chaining via environment variables (`authToken`, `bookingId`).

## Files

- `Restful Booker API Tests.postman_collection.json` — the Postman collection (import into Postman to run)
- `Restful Booker Env.postman_environment.json` — the environment used by the collection

## How to run

1. Open Postman
2. Import both JSON files (**Import** button)
3. Select "Restful Booker Env" as the active environment
4. Run requests in order: Create Auth Token → Create Booking → Get Booking → Update Booking → Delete Booking

## Known limitation

The `PUT /booking/{id}` (Update) endpoint on this public Heroku-hosted demo API intermittently returns `405 Method Not Allowed`, even with correct authentication and a correctly formatted request. This was verified by testing the same request repeatedly and cross-checking the authentication method. GET, POST, and DELETE operations are consistently reliable. This is a known limitation of the free-tier demo service, not an issue with the test design.

## Tech stack

- Postman (manual/exploratory testing with assertions)
- Playwright + TypeScript (automated API testing — in progress)

## Author

**Yashi Dwivedi**
QA Analyst transitioning into automation testing.
[GitHub](https://github.com/yashi-dwivedi)
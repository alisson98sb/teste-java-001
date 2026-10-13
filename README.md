# Technical Assessment — Java + Spring Boot

## REST API for Debt Management

> Assignment reconstructed from the course screenshots and organized in Markdown. This document describes the exercise to be implemented. The implementation checkpoints at the end were added as a progress tracker and are not part of the original assignment.

## 1. Objective

Develop a backend application using Java and Spring Boot to register and manage debtors' debts through a REST API.

## 2. Functional Requirements

| Code | Requirement | Description |
| --- | --- | --- |
| RF01 | Create a debt | Allow a new debt to be registered. |
| RF02 | Retrieve a debt | Allow a debt to be retrieved by its identifier. |
| RF03 | List debts | Allow all registered debts to be retrieved. |
| RF04 | Update a debt | Allow the information of an existing debt to be updated. |
| RF05 | Delete a debt | Allow an existing debt to be deleted. |
| RF06 | Debtor's CPF | Store the CPF associated with the debt. |

CPF is the Brazilian individual taxpayer identification number.

## 3. Debt Data

Each debt must contain at least the following fields. Field names are preserved from the original assignment.

| Field | Suggested Type | Description |
| --- | --- | --- |
| `id` | `Long` | Unique identifier of the debt. |
| `cpfDevedor` | `String` | Debtor's CPF. |
| `valorPego` | `BigDecimal` | Amount originally borrowed by the debtor. |
| `valorComJuros` | `BigDecimal` | Debt amount including interest. |
| `valorComDesconto` | `BigDecimal` | Debt amount after applying the discount. |

## 4. REST API

The application must provide REST endpoints for CRUD operations. The structure below is a suggestion; equivalent endpoint structures are acceptable as long as all operations are supported.

| Method | Endpoint | Purpose |
| --- | --- | --- |
| `POST` | `/dividas` | Create a debt. |
| `GET` | `/dividas/{id}` | Retrieve a debt by ID. |
| `GET` | `/dividas` | List all debts. |
| `PUT` | `/dividas/{id}` | Update a debt. |
| `DELETE` | `/dividas/{id}` | Delete a debt. |

## 5. Request Example

Example request body for creating a debt:

```json
{
  "cpfDevedor": "12345678900",
  "valorPego": 1000.00,
  "valorComJuros": 1200.00,
  "valorComDesconto": 1100.00
}
```

## 6. Technical Requirements

- Use **Java**.
- Use **Spring Boot**.
- Provide a REST API.
- Persist the data. A relational database of your choice may be used.
- Use **BigDecimal** for monetary values.
- Organize the project clearly, separating responsibilities into layers where applicable.
- Handle HTTP status codes and API errors appropriately.
- Provide instructions for running the project.

## 7. Expected Validations

- CPF must be provided.
- Monetary values must be valid and non-negative.
- A nonexistent debt must result in an appropriate HTTP response.
- Update and delete operations must check whether the record exists.
- The API must return HTTP responses consistent with each operation.

## 8. Optional Enhancements

The following items are not mandatory, but may be implemented to demonstrate additional knowledge:

- Unit tests and/or integration tests.
- API documentation with OpenAPI/Swagger.
- Docker/Docker Compose.
- Database migrations.
- Pagination when listing debts.
- Filters or queries by CPF.
- Validation using Bean Validation.
- Global exception handling.
- Logging and well-organized application configuration.

## 9. Deliverables

Deliver the project's source code in a Git repository containing a README with the instructions required to configure, run, and test the application.

The README must also list the technologies used and, if necessary, the database configuration parameters.

## 10. Implementation Checkpoints

Mark an item as complete by changing `- [ ]` to `- [x]`. Items start unchecked; mark them after verifying the corresponding behavior.

### Checkpoint 1 — Project Setup

- [x] Create the Spring Boot project with the required dependencies.
- [x] Align the Java version in the project, Maven configuration, and IntelliJ SDK.
- [x] Confirm that Maven reloads and builds the project successfully.
- [ ] Organize packages to separate API, business logic, and persistence responsibilities.

### Checkpoint 2 — Database and Local Environment

- [x] Add `docker-compose.yml` and `.env` for PostgreSQL.
- [x] Start PostgreSQL and confirm that it is healthy.
- [x] Configure the PostgreSQL driver and Spring datasource settings.
- [ ] Start the application successfully with a working database connection.
- [ ] Verify that database data survives container recreation using the configured volume.

### Checkpoint 3 — Debt Model and Persistence

- [ ] Create the debt entity with all five fields from Section 3.
- [ ] Use `BigDecimal` for all monetary fields.
- [ ] Configure the unique identifier and its generation strategy.
- [ ] Configure table creation through JPA or database migrations.
- [ ] Create the repository and verify that a debt can be saved and retrieved.

### Checkpoint 4 — CRUD Operations

- [ ] Implement debt creation — `POST /dividas` (RF01 and RF06).
- [ ] Implement retrieval by ID — `GET /dividas/{id}` (RF02).
- [ ] Implement debt listing — `GET /dividas` (RF03).
- [ ] Implement debt updates — `PUT /dividas/{id}` (RF04).
- [ ] Implement debt deletion — `DELETE /dividas/{id}` (RF05).

### Checkpoint 5 — Validation and Error Handling

- [ ] Reject requests without a CPF.
- [ ] Validate monetary values and reject negative amounts.
- [ ] Return an appropriate HTTP response when a debt is not found.
- [ ] Check record existence before updating or deleting a debt.
- [ ] Return coherent HTTP status codes for successful and failed operations.
- [ ] Return understandable API error messages.

### Checkpoint 6 — Functional Verification

- [ ] Create a debt using the example JSON and verify the persisted values.
- [ ] Retrieve the created debt by ID and confirm that it appears in the list.
- [ ] Update the debt and verify the saved changes.
- [ ] Delete the debt and verify that it can no longer be retrieved.
- [ ] Verify the response when the debt list is empty.
- [ ] Verify missing CPF, negative amounts, and nonexistent IDs.

### Checkpoint 7 — Optional Enhancements

These items are optional and are not required to complete the core exercise.

- [ ] Add pgAdmin and register the PostgreSQL server.
- [ ] Add unit tests and/or integration tests.
- [ ] Document the API with OpenAPI/Swagger.
- [ ] Add database migrations.
- [ ] Add pagination to the debt listing endpoint.
- [ ] Add filtering or queries by CPF.
- [ ] Use Bean Validation for request validation.
- [ ] Implement global exception handling.
- [ ] Add useful logs and organize application configuration.

### Checkpoint 8 — Documentation and Delivery

- [ ] Document the technologies and versions used.
- [ ] Document database configuration and environment variables.
- [ ] Document how to start the database and application.
- [ ] Document how to test the API, including request examples.
- [ ] Keep local credentials out of Git and provide an `.env.example` for setup.
- [ ] Verify setup and execution by following the README from a clean checkout.
- [ ] Publish the source code in a Git repository.

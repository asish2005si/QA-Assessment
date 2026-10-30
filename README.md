# QA Assessment – Manual Testing & API Testing

## 1. Project Overview

This repository contains my Quality Assurance (QA) assessment work, covering manual website testing and REST API testing.

The purpose of this assessment is to demonstrate my practical understanding of software testing, including test case design, functional testing, positive and negative testing, API validation, defect identification, test execution and documentation.

The assessment covers two applications:

1. **SauceDemo** – Manual functional testing of an e-commerce web application.
2. **JSONPlaceholder** – REST API testing using Postman.

Throughout the assessment, I focused on understanding expected application behaviour, executing test scenarios, comparing actual results with expected results, and documenting findings clearly.

---
api testing Tests cases link:https://docs.google.com/spreadsheets/d/1y_p6gvdicFqcEL3vYmKLh7Wpb8_zM7Cm1zMxknC6Psk/edit?usp=sharing
## 2. Project Objectives

* Understand application functionality and requirements.
* Prepare structured test cases.
* Perform positive and negative testing.
* Validate user workflows and application behaviour.
* Test REST API endpoints using Postman.
* Verify HTTP status codes and JSON responses.
* Identify and document defects.
* Maintain test execution records and screenshots.
* Prepare professional testing documentation.

---

## 3. Applications Under Test

### A. Website Testing – SauceDemo

**Application:** Swag Labs (SauceDemo)

**Website:** https://www.saucedemo.com/

SauceDemo is a demo e-commerce application used to practise manual and automated software testing.

#### Testing Scope

| Module               | Testing Activities                                          |
| -------------------- | ----------------------------------------------------------- |
| Login                | Valid login, invalid login and locked-out user validation   |
| Products             | Product listing, product details and image verification     |
| Sorting              | Product sorting and filter functionality                    |
| Add to Cart          | Adding products and checking cart badge                     |
| Remove from Cart     | Removing selected products                                  |
| Shopping Cart        | Product details, quantity and price verification            |
| Checkout Information | First name, last name and postal code validation            |
| Checkout Overview    | Product details, subtotal, tax and total verification       |
| Order Completion     | Finish button and order confirmation                        |
| Navigation           | Menu, logout, continue shopping and back-home functionality |
| Performance          | Page loading and response behaviour                         |

#### Test Accounts

The following public demo accounts were used during testing:

| Username                | Purpose                                |
| ----------------------- | -------------------------------------- |
| standard_user           | Standard functionality testing         |
| locked_out_user         | Login restriction testing              |
| problem_user            | UI and functional issue testing        |
| performance_glitch_user | Performance behaviour testing          |
| error_user              | Error and functional behaviour testing |
| visual_user             | Visual and UI testing                  |

**Password:** `secret_sauce`

#### Important Testing Observations

During testing, the following unexpected behaviours were observed:

1. Product images displayed incorrectly under `problem_user`.
2. Sorting under `error_user` displayed an unexpected error message.
3. The Last Name field did not accept keyboard input under `error_user`.
4. The Finish button did not complete the checkout process under `error_user`, as observed during testing.
5. The Remove button below a product did not behave as expected under `error_user`; this behaviour requires precise reproduction evidence.
6. The `performance_glitch_user` account showed slower loading and navigation behaviour in several areas.

These observations should be supported by individual bug reports and screenshots.

Google sheets link:https://docs.google.com/spreadsheets/d/1GZOnHi9mjbnBYDPCZe9is4zmQzNH48NDDqgjAg75lH8/edit?usp=sharing
Bug report link :https://docs.google.com/document/d/1I0VNVzUM3WEXiu8ilzHIEbofKQtVAR9Z2WA449cKPlA/edit?usp=sharing
---

### B. API Testing – JSONPlaceholder

**API Name:** JSONPlaceholder

**Base URL:** https://jsonplaceholder.typicode.com/

**API Documentation:** https://jsonplaceholder.typicode.com/guide/

JSONPlaceholder is a public simulated REST API used for practising API testing without requiring authentication.

#### Testing Tool

Postman

#### API Testing Scope

| Test ID | Method | Endpoint            | Test Scenario                    |
| ------- | ------ | ------------------- | -------------------------------- |
| API-01  | GET    | `/posts`            | Retrieve all posts               |
| API-02  | GET    | `/posts/1`          | Retrieve a specific post         |
| API-03  | POST   | `/posts`            | Create a new post                |
| API-04  | POST   | `/posts`            | Submit an empty JSON body        |
| API-05  | GET    | `/posts/101`        | Verify post persistence          |
| API-06  | PUT    | `/posts/1`          | Update an existing post          |
| API-07  | PATCH  | `/posts/1`          | Update a specific field          |
| API-08  | DELETE | `/posts/1`          | Delete an existing post          |
| API-09  | GET    | `/posts?userId=1`   | Filter posts by user ID          |
| API-10  | GET    | `/posts/1/comments` | Retrieve comments for a post     |
| API-11  | GET    | `/posts/9999`       | Verify invalid post ID behaviour |

#### API Testing Approach

For each API request, I checked:

* HTTP method and endpoint.
* Request URL.
* Request body, where applicable.
* HTTP status code.
* Response body.
* JSON response structure.
* Expected versus actual results.
* Response time.

#### API Execution Results

The following results reflect the API requests executed so far.

| Test ID | Scenario                | Expected Status | Actual Status | Result                |
| ------- | ----------------------- | --------------- | ------------- | --------------------- |
| API-01  | GET All Posts           | 200             | 200           | Pass – visible checks |
| API-02  | GET Single Post         | 200             | 200           | Pass                  |
| API-03  | POST Create Post        | 201             | 201           | Pass                  |
| API-04  | POST Empty Body         | Observe         | 201           | Observed              |
| API-05  | Verify Post Persistence | 404             | 404           | Pass                  |
| API-06  | PUT Update Post         | 200             | 200           | Pass                  |
| API-07  | PATCH Update Title      | 200             | 200           | Pass                  |
| API-08  | DELETE Existing Post    | 200             | Pending       | Not Executed          |
| API-09  | Filter Posts by User ID | 200             | Pending       | Not Executed          |
| API-10  | Retrieve Post Comments  | 200             | Pending       | Not Executed          |
| API-11  | Invalid Post ID         | 404             | Pending       | Not Executed          |

#### API Testing Observations

* GET requests successfully returned the requested data.
* A valid POST request returned `201 Created` with a generated ID.
* An empty JSON object was accepted by the POST endpoint.
* The empty-body behaviour was recorded as an observation because mandatory-field validation was not specified.
* GET `/posts/101` returned `404 Not Found`, demonstrating that the simulated POST operation did not permanently store the created post.
* PUT and PATCH returned the requested updated data.

**API Limitation:** JSONPlaceholder simulates write operations. POST, PUT, PATCH and DELETE operations do not permanently modify the stored resources.

---

## 4. Testing Methodology

I followed a structured testing approach throughout the assessment.

### Functional Testing

Verified that application features behaved according to their expected functionality.

### Positive Testing

Executed valid inputs and normal user workflows.

### Negative Testing

Checked application behaviour using invalid credentials, incomplete inputs and unexpected values.

### Boundary Testing

Considered input limits and validation behaviour where applicable.

### Regression Testing

Rechecked related functionality after identifying unexpected behaviour.

### API Testing

Validated HTTP methods, status codes, request bodies and response data using Postman.

---

## 5. Bug Reporting

Unexpected behaviours identified during testing were documented with reproducible steps.

Each bug report includes:

* Bug ID
* Bug title
* Module
* Description
* Preconditions
* Steps to reproduce
* Expected result
* Actual result
* Severity
* Priority
* Status
* Screenshot evidence

Only reproducible and evidence-supported issues should be treated as confirmed defects.

---

## 6. Tools & Technologies

| Tool            | Purpose                                         |
| --------------- | ----------------------------------------------- |
| Postman         | REST API testing                                |
| Microsoft Excel | Test case and result documentation              |
| Google Sheets   | Test execution tracking                         |
| GitHub          | Project documentation and assessment submission |
| Web Browser     | Manual website testing                          |
| JSON            | API request and response format                 |

---

## 7. Repository Structure

```text
QA-Assessment/
│
├── Website-Testing/
│   ├── SauceDemo-Test-Cases.xlsx
│   ├── SauceDemo-Test-Results.xlsx
│   └── Screenshots/
│
├── API-Testing/
│   ├── API-Test-Cases.xlsx
│   ├── API-Test-Execution-Results.xlsx
│   ├── Postman-Collection.json
│   └── Screenshots/
│
├── Bug-Reports/
│   ├── Bug-Reports.xlsx
│   └── Bug-Reports.pdf
│
├── Test-Summary.pdf
│
└── README.md
```

*The folder structure should be updated to match the actual files uploaded to GitHub.*

---

## 8. Test Execution Summary

This assessment covers two areas of software testing:

**Website Testing**

* Login and authentication.
* Product listing and sorting.
* Shopping cart operations.
* Checkout and order completion.
* UI and performance observations.

**API Testing**

* GET, POST, PUT, PATCH and DELETE methods.
* Positive and negative test scenarios.
* Request and response validation.
* HTTP status code verification.

API execution is currently partially completed. The remaining API scenarios must be executed and their actual results recorded before final submission.

---

## 9. Learning Outcomes

Through this assessment, I gained practical experience in:

* Understanding application functionality.
* Designing structured test cases.
* Executing manual test scenarios.
* Identifying and documenting defects.
* Working with different HTTP methods.
* Using Postman for API testing.
* Validating JSON responses.
* Understanding simulated API behaviour.
* Maintaining testing documentation.
* Organizing QA deliverables using GitHub.

---

## 10. Conclusion

This assessment provided an opportunity to apply my software testing knowledge to both a web application and REST APIs.

By testing SauceDemo, I practised validating real user workflows such as login, product selection, cart management and checkout.

Through JSONPlaceholder, I gained practical experience in sending API requests, validating responses, testing different HTTP methods and documenting API behaviour.

My focus throughout the assessment was to follow a systematic testing approach, maintain accurate execution records and document findings in a clear and professional manner.

---

**Prepared by:** Asish Kumar Padhy

**Role:** QA / Software Testing Candidate

**Assessment:** Manual Website Testing & API Testing

**Tools:** Postman, Excel, Google Sheets and GitHub

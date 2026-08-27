# Panda-Lite API System Testing Report

**Course:** [Software Testing]

**Assignment:** System Testing

**Group:** [Team D2]

**Submission Date:** [8/27/2026]

# 1. Team Plan

## 1.1 Team Members

| No. | Student Name | Student ID | Responsibility |
|---|---|---|---|
| 1 | [Mania Sultana] | [011212038] | [Authentications,Restaruants, Orders ] |
| 2 | [Taspia Akter Epou] | [011212163] | [Orders, Rating] |
| 3 | [Sumaiya Islam Ety] | [011212164] | [Restaruants-menu,id] |
| 4 | [Joysree Bardhan] | [011221189] | [Orders-Claim] |

## 1.2 Individual Contribution

**Name:** Mania Sultana

**Student ID:** 011212038

**Assigned Module:** Rating API

### My Responsibilities

- Tested the Rating API endpoints using Postman.
- Created positive and negative test cases for restaurant ratings.
- Validated HTTP status codes, response structure, fields, and query parameters.
- Identified and documented API defects with screenshots and test evidence.

# 2. Testing Scope

The Panda-Lite API was tested using Postman.

The testing covered:

- Authentication
- Restaurants
- Orders
- Ratings

The testing included:

- Positive test cases
- Negative test cases
- Status code validation
- Response body validation
- Required field validation
- Query parameter validation
- Error response validation
- Postman test scripts

# 3. Test Environment

| Item | Details |
|---|---|
| Testing Tool | Postman |
| Application | Panda-Lite API |
| Environment | Panda-Lite - D2 |
| API Type | REST API |
| Authentication | Bearer Token |
| Headers | Personal key |

# 4. Test Cases

## 4.1 Test Case Summary

| Test Case ID | Test Case | Endpoint | Expected Status | Actual Status | Verdict |
|---|---|---|---:|---:|---|
| TC-01 | Register new user | POST/{{baseUrl}}/auth/register | 200 | 200 | PASS|
| TC-02 | Register User Already Exists | POST/{{baseUrl}}/auth/register | 409 | 409  | PASS|
| TC-03 | Register User type |  POST/{{baseUrl}}/auth/register | 400 | 400 | PASS |
| TC-04 | Register User role remove |  POST/{{baseUrl}}/auth/register | 400 | 400 | PASS |
| TC-05 | Register User password short |  POST/{{baseUrl}}/auth/register | 400 | 400 | PASS |
| TC-06 | Login User | Post/{{baseUrl}}/auth/login  | 200 | 200| PASS |
| TC-07 | Login User wrong pass | Post/{{baseUrl}}/auth/login | 401 | 401 | PASS/Fail |
| TC-08 | Login User not exist |  Post/{{baseUrl}}/auth/login | 401 | 401 | PASS/Fail |
| TC-09| Login User Missing Credentials|  Post/{{baseUrl}}/auth/login  | 400 | 400 | PASS/Fail |
| TC-10| Get all Restaruants| GET/{{baseUrl}}/restaurants  | 200| 200 | PASS|
| TC-11| Create Restaruants | POST/{{baseUrl}}/restaurants  | 201| 201 | PASS|
| TC-12| Get all Restaruants ID | GET/{{baseUrl}}/restaurants  | 200| 200 | PASS|
| TC-13| Get all Restaruants ID No token | GET/{{baseUrl}}/restaurants/e1c1c98f-f852-4670-886d-fece05da2099  | 401| 401 | PASS|
| TC-14| Get all Restaruants ID No Found | GET/{{baseUrl}}/restaurants/00000000-0000-0000-0000-000000000000 | 404| 404 | PASS|
| TC-15| Get all Restaruants Open status | PATCH/{{baseUrl}}/restaurants/e1c1c98f-f852-4670-886d-fece05da2099 | 201| 201| PASS|
| TC-16| Get all Restaruants menu Item | POST/{{baseUrl}}/restaurants/e1c1c98f-f852-4670-886d-fece05da2099/menu | 201| 201| PASS| 
| TC-17| Restaruants ID Missing Token | PATCH/{{baseUrl}}/restaurants/e1c1c98f-f852-4670-886d-fece05da2099 | 401| 401| PASS|
| TC-18| Restaruants ID Not Found  | Patch/{{baseUrl}}/restaurants/00000000-0000-0000-0000-000000000000 | 404| 404| PASS|
| TC-19| Restaurants  Bug restaurants name any can  set | PATCH/{{baseUrl}}/restaurants/e1c1c98f-f852-4670-886d-fece05da2099 | 200| 200| PASS|
| TC-20|No Token |Get/{{baseUrl}}/restaurants | 401| 401| PASS|
| TC-21|Invaild Query Params |{{baseUrl}}/restaurants?sort_by=wrong| 400| 400 | PASS|
| TC-22|Restaurants Order Status | PATCH/{{baseUrl}}/orders/c3969e61-5e30-4bb9-a711-6e586ee00c7b/status | 200| 200| PASS|
| TC-23|Restaurants Order Status missing Token | PATCH/{{baseUrl}}/orders/c3969e61-5e30-4bb9-a711-6e586ee00c7b/status | 401| 401| PASS|
| TC-24|Restaurants Order Status invaild check| PATCH/{{baseUrl}}/orders/c3969e61-5e30-4bb9-a711-6e586ee00c7b/status | 404| 404| PASS|
| TC-25|Order Status required | PATCH/{{baseUrl}}/orders/c3969e61-5e30-4bb9-a711-6e586ee00c7b/status | 400| 400| PASS|
| TC-26|Order Status preparing | PATCH/{{baseUrl}}/orders/c3969e61-5e30-4bb9-a711-6e586ee00c7b/status | 400| 400| PASS|
| TC-27|Order Status ready for pickup | PATCH/{{baseUrl}}/orders/c3969e61-5e30-4bb9-a711-6e586ee00c7b/status | 200| 200| PASS|
| TC-28|Order Status ready for picked_up | PATCH/{{baseUrl}}/orders/c3969e61-5e30-4bb9-a711-6e586ee00c7b/status | 200| 200| PASS|
| TC-29|Order Status delivered| PATCH/{{baseUrl}}/orders/c3969e61-5e30-4bb9-a711-6e586ee00c7b/status | 200| 200| PASS|
| TC-30|Order cancelled| PATCH/ {{baseUrl}}/orders/db8a65cc-f179-44a4-ae94-12a7eb94ca9b/cancel | 200| 200| PASS|
| TC-31|Order cancelled missing token | PATCH/ {{baseUrl}}/orders/db8a65cc-f179-44a4-ae94-12a7eb94ca9b/cancel | 401| 401| PASS|
| TC-32|Order cancelled Not found  | PATCH/ {{baseUrl}}/orders/db8a65cc-f179-44a4-ae94-12a7eb94ca9b/cancel | 404| 404| PASS|
| TC-33|Order cancelled fee include bug  | PATCH/ {{baseUrl}}/orders/db8a65cc-f179-44a4-ae94-12a7eb94ca9b/cancel | 404| 404| PASS/Fail|
| TC-34|Order rating  only Owner  | PATCH/ {{baseUrl}}/orders/db8a65cc-f179-44a4-ae94-12a7eb94ca9b/rate| 403| 403| PASS|
| TC-35|Order  only claim rider  | PATCH/ {{baseUrl}}/orders/c3969e61-5e30-4bb9-a711-6e586ee00c7b/claim | 200| 200| PASS|
| TC-36| Oder customer rating | post/{{baseUrl}}/orders/c3969e61-5e30-4bb9-a711-6e586ee00c7b/rate| 201| 201| PASS|
| TC-37| restaruant customer rating check | GEt/{{baseUrl}}/orders/c3969e61-5e30-4bb9-a711-6e586ee00c7b/rate| 200| 200| PASS|
| TC-38| restaruant customer rating check  sort by ASC | GEt/{{baseUrl}}/orders/c3969e61-5e30-4bb9-a711-6e586ee00c7b/rate| 200| 200| PASS|
| TC-39| restaruant customer rating check  sort by DESC&  value | GEt/{{baseUrl}}/orders/c3969e61-5e30-4bb9-a711-6e586ee00c7b/rate| 200| 200| PASS|
| TC-40| restaruant customer rating check  sort by DESC&   wrong value | GEt/{{baseUrl}}/orders/c3969e61-5e30-4bb9-a711-6e586ee00c7b/rate| 400| 400| PASS|





## 4.2 Detailed Test Cases



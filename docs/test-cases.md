# Test Case FakeStoreAPI

## Info
- Collection: FakeStoreAPI - Tests
- Environment: FakeStoreAPI Env
- Base URL: {{base_url}}



## Test Cases

| ID | Endpoint | Method | Type | Steps | Expected |
|----|----------|--------|------|-------|----------|
| TC-GET-01 | /products | GET | Positive | GET /products | 200, response = array, item schema valid |
| TC-GET-02 | /products/:id | GET | Positive | GET /products/1 | 200, response object, matches schema |
| TC-GET-03 | /products/999999 | GET | Negative | GET invalid id | 404 or empty / controlled response |
| TC-POST-01 | /products | POST | Positive | POST valid body (title, price, description, image, category) | 201/200, response has id, response matches schema, env.product_id set |
| TC-POST-02 | /products | POST | Negative | POST missing required fields | 400/422 or response lacking required props |
| TC-PUT-01 | /products/:id | PUT | Positive | PUT update (use env.product_id) | 200, response contains updated fields |
| TC-PUT-02 | /products/999999 | PUT | Negative | PUT invalid id | 404 or error-like response |
| TC-DELETE-01 | /products/:id | DELETE | Positive | DELETE env.product_id | 200/204, response shows deleted id or success, env.product_id unset |
| TC-DELETE-02 | /products/999999 | DELETE | Negative | DELETE invalid id | 404 or harmless response |



## Notes
- Precondition: For PUT/DELETE tests, ensure `product_id` exists; run POST Create Product first or set `product_id` manually.
- Use JSON Schema file `schemas/product-schema.json` for contract validation.
- Maintain test data separation: do not use production data.

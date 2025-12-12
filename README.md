# FakeStore API Automation & Contract Testing

Project: API automation and contract testing for FakeStoreAPI using Postman and Newman

## What's included
- Postman Collection: `collections/fakestore-collection.json`
- Postman Environment: `environments/fakestore-env.json`
- JSON Schema: `schemas/product-schema.json`
- Test cases: `docs/test-cases.md`
- GitHub Actions workflow: `.github/workflows/api-tests.yml`
- Reports: generated into `reports/` 

## Prerequisites
- Node.js & npm
- Newman (`npm install -g newman newman-reporter-htmlextra`)
- Postman (for development & manual debugging)
- Git & GitHub account

## How to import into Postman
1. Open Postman → File → Import → choose `collections/fakestore-collection.json`
2. Import environment: **Environments → Import** → choose `environments/fakestore-env.json`
3. Choose environment `FakeStoreAPI Env` in the top right.

## How to run locally with Newman
```bash
# install newman if not installed
npm install -g newman newman-reporter-htmlextra

# run collection (from repo root)
newman run collections/fakestore-collection.json -e environments/fakestore-env.json -r cli,htmlextra --reporter-htmlextra-export reports/report.html

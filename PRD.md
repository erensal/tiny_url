# Product Requirements Document: Serverless URL Shortener

## 1. Executive Summary

A high-performance, cloud-native URL shortening service built on AWS. The project emphasizes professional backend engineering practices, including serverless architecture, cost-optimization via storage tiering, and rigorous design documentation.

## 2. Release Cadence

### Phase 1: MVP (Minimum Viable Product)

**Goal:** Core functional redirection.

- **Shorten API:** `POST /shorten` accepting a long URL and returning a Base62 encoded string.
- **Redirect API:** `GET /{short_code}` returning an HTTP 302 redirect.
- **Persistence:** DynamoDB table for key-value storage.
- **Infrastructure:** AWS SAM for deployment.

### Phase 2: MMP (Minimum Marketable Product)

**Goal:** Security, customization, and usability.

- **Custom Aliases:** Allow users to request specific short strings (e.g., `/my-link`).
- **Validation:** Input sanitization and reserved word filtering.
- **Rate Limiting:** API Gateway throttling to prevent abuse.
- **Documentation:** Automated Swagger/OpenAPI documentation.

### Phase 3: MLP (Minimum Lovable Product)

**Goal:** "Google-level" engineering and cost-efficiency.

- **Storage Tiering:** Automated archival of inactive links to S3 via EventBridge and Lambda.
- **Analytics:** Basic click-tracking (hit counts).
- **TTL (Time to Live):** Support for expirable links.

## 3. Technical Constraints

- **Cloud Provider:** AWS (Free Tier Optimized).
- **Language:** Python 3.12+.
- **Architecture:** 100% Serverless (Lambda, API Gateway, DynamoDB).
- **Documentation:** Every major feature must have a corresponding Design Doc in `/designs`.

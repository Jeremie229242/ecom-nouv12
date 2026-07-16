# Taste (Continuously Learned by [CommandCode][cmd])

[cmd]: https://commandcode.ai/

# Social Oauth
- When adding a social OAuth integration (e.g., GitHub, Google), follow this structure: 1) Create `src/lib/social-oauth/` with encryption (AES-256-GCM), state (HMAC-signed CSRF), and an index.ts with OAuth URLs/token exchange/refresh/user API helpers, 2) Create `src/models/{provider}-account.model.ts`, 3) Create `src/services/{provider}.service.ts` with connect/callback/getAccessToken/disconnect, 4) Create `src/controllers/{provider}.controller.ts` with Zod validation, 5) Create `src/routes/{provider}.route.ts`, 6) Update env.config.ts, routes/index.ts, and .env/.env.example. Confidence: 0.70

# Resource Scaffolding
- When scaffolding a new resource (e.g., session, product, blog), follow this pattern: 1) Controllers use `asyncHandler` wrapper, and protected routes extract `_id` from `req.user`, 2) Validation schemas go in `src/validators/`, 3) Services export scaffolded function stubs that return placeholder text responses, 4) Routes use `passportAuthenticateJwt` middleware for protected endpoints. Confidence: 0.70
- Controllers must include a `message` field in every JSON response (e.g., `{ message: "Sessions retrieved successfully", sessions }`), not just return data without a message. Follow the existing pattern from auth and github controllers. Confidence: 0.65

# node.js-scaffolding
See [node.js-scaffolding/taste.md](node.js-scaffolding/taste.md)

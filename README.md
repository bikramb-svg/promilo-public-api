# promilo-public-api
Public API for discovering courses, colleges, and education programs on Promilo. Provides structured access to course listings, institutions, locations, fees, and related details for education discovery and career guidance platforms.
Promilo is an education discovery and career guidance platform that helps users explore courses, colleges, and institutions across India and selected global destinations.

The Promilo Public API provides structured, programmatic access to this data so developers, platforms, and AI systems can build discovery tools, recommendation engines, and education-focused applications without scraping or manual aggregation.

This API is intentionally simple and keyword-driven.

What this API provides

Using the Promilo Public API, you can:

- Search and discover courses across streams and levels
- Identify colleges and institutions offering specific programs

Access structured details like:

- college name
- course duration
- delivery mode
- fees (where available)
- location
- accreditations, rankings, and entrance exams

Common use cases include:

- Education comparison platforms
- Admission counselling tools
- Career guidance and discovery apps
- AI-powered assistants answering education-related queries
- API specification (OpenAPI)

The complete OpenAPI specification is available here:

👉 https://api.promilo.com/openapi.json

This file defines all available endpoints, query parameters, and response schemas in a machine-readable format and can be directly consumed by tools like Swagger UI, Postman, and AI systems.

Base URL
https://api.promilo.com


All API requests are made relative to this base URL.

Available endpoint
Search courses
GET /courses


This endpoint allows keyword-based discovery of courses.

Query parameters

query (string, optional)
Used to search courses by name, stream, or common terms (e.g. BCA, MBA, B.Tech).

page_number (integer, optional, default: 0)
Used for pagination.

Example request
curl -X GET "https://api.promilo.com/courses?keyword=BCA&page_number=0"

Example response (simplified)
{
  "count": 1,
  "courses": [
    {
      "campaignId": "8a81808699e1e8b70199f0e54553304b",
      "description": "Bachelor of Computer Applications program focused on software fundamentals.",
      "deliveryMode": "Regular / Offline",
      "collegeName": "Techno International New Town",
      "stream": "Computer Applications",
      "subStream": "BCA",
      "location": "Kolkata",
      "collegeFees": "3.20 Lakhs",
      "courseDuration": "3 YEAR",
      "courseUrl": "[https://www.promilo.com/course/bca-tint](https://www.promilo.com/courses-description/it-software/bca/bachelor-of-computer-applications-bca/techno-international-new-town-6)"
    }
  ]
}

How this API is typically used

Because the API is course-centric, most applications:

Perform keyword-based searches

Apply client-side filtering on fields like:

location

collegeName

subStream

Group results to build pages such as:

BCA colleges in Kolkata

MBA programs by city

Engineering courses by stream

This keeps the API flexible while allowing different products to shape their own discovery logic.

Examples & use cases

More real-world examples are available in:

docs/use-cases.md


These include:

Finding BCA colleges in Kolkata

Exploring MBA programs by keyword

Using accreditations, rankings, and entrance exams for decision support

Rate limits & usage

Reasonable rate limits may apply to ensure fair usage and platform stability.

If you are building a high-volume integration or partner application, it’s recommended to coordinate usage expectations in advance.

Errors

The API uses standard HTTP status codes and structured JSON responses.

Common responses include:

400 – Invalid or missing parameters

401 / 403 – Authentication or access issues

404 – Resource not found

429 – Rate limit exceeded

Versioning

The API currently follows a stable, forward-compatible approach.

Any breaking changes will be communicated clearly and ahead of time.

Security

If you discover a potential security issue, please report it responsibly.

Do not open a public GitHub issue for vulnerabilities.
Report concerns via:

👉 https://www.promilo.com/contact-us

More details are available in SECURITY.md.

License

This repository is licensed under the MIT License.

This license applies to the documentation, OpenAPI specification, and examples in this repository.
API usage and data access remain subject to Promilo’s platform terms and policies.

About Promilo

Website: https://www.promilo.com

Contact: https://www.promilo.com/contact-us

If something in the API or documentation feels unclear, that feedback is genuinely useful.
More real-world examples are available in [docs/use-cases.md](docs/use-cases.md).


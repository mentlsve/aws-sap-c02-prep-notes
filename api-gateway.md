## API Gateway

Deployment options:
* **Edge-optimized endpoint**: Via CloudFront. Reduced latency for access from around the world.
* **Regional endpoint**: For access from services in same region
* **Private endpoint**: For access from services in same VPC

Structure of an API:
* Method Request (HTTP methods)
* Integration Request (HTTP, HTTP_PROXY, LAMBDA, LAMBDA_PROXY, MOCK)
* Endpoint
* Integration Response (CONVERT, PASSTHROUGH)
* Method Response (HTTP status codes, response bodies)

Caching:
* Can be enabled at Stage level and caches endpoint response

Throttling:
* Steady-state request rate. Default 10,000 requests per second.
* Maximum concurrent requests. 5,000 requests.
* Exceeding limits will result in `429 Too Many Requests`

Usage Plans and API Keys:

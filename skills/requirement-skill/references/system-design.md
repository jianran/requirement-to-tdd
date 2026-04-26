# System interactive flow and API specification design

Use this reference when designing system interactions, API endpoints, and data flow specifications for new features.

## 1. Design system interaction flow

Start with a high-level diagram of component relationships:

```
User Interface
    ↓ (HTTP/API calls)
API Gateway/Load Balancer
    ↓ (routing)
Application Server
    ↓ (business logic)
Domain Services
    ↓ (data operations)
Database/Storage
    ← (responses flow back up)
```

Identify key interaction points:

- **Entry points** — how users or systems initiate the flow
- **Processing layers** — validation, transformation, business rules
- **Data boundaries** — where data crosses system boundaries
- **External dependencies** — third-party services, databases, caches
- **Exit points** — responses, events, notifications, or side effects

## 2. Define API specifications

For each API endpoint, specify:

### Endpoint structure
```
Method: POST|GET|PUT|DELETE
Path: /api/v1/resource/{id}
Authentication: Bearer token | API key | None
Rate limiting: 100 requests/minute per user
```

### Request format
```json
{
  "field1": "string (required)",
  "field2": "number (optional, default: 0)",
  "nestedObject": {
    "subfield": "array of strings"
  }
}
```

### Response format
```json
{
  "success": true,
  "data": {
    "id": "uuid",
    "createdAt": "ISO 8601 timestamp",
    "result": "processed data"
  },
  "errors": null
}
```

### Error responses
```json
{
  "success": false,
  "data": null,
  "errors": [
    {
      "code": "VALIDATION_ERROR",
      "message": "Field 'email' is required",
      "field": "email"
    }
  ]
}
```

## 3. Specify data models and validation

Define schemas for all data structures:

### Input validation rules
- Required vs optional fields
- Data types and formats
- Length constraints
- Allowed value ranges
- Cross-field validation rules

### Output schemas
- Consistent field naming
- Nullable fields clearly marked
- Pagination for list endpoints
- Metadata inclusion (timestamps, version info)

## 4. Document integration points

For each external system integration:

- **Protocol** — REST, GraphQL, gRPC, message queue, webhook
- **Authentication** — API keys, OAuth, certificates, JWT
- **Error handling** — retry logic, circuit breakers, fallback behavior
- **Data transformation** — mapping between internal and external formats
- **Monitoring** — health checks, metrics, alerting

## 5. Define state transitions and business rules

Document how the system moves between states:

### State diagram
```
Initial State
    ↓ (trigger event)
Intermediate State
    ↓ (validation/business rules)
Final State
    ↓ (side effects)
```

### Business rules
- Preconditions for state changes
- Validation rules at each step
- Error conditions and recovery
- Audit logging requirements

## 6. Consider cross-cutting concerns

Address these in the design:

- **Security** — authentication, authorization, input sanitization
- **Performance** — caching, async processing, optimization opportunities
- **Monitoring** — logging, metrics, tracing
- **Scalability** — horizontal scaling, database sharding
- **Backward compatibility** — versioning, migration strategies

## 7. Create implementation checklist

Before coding, verify:

- All user touchpoints are covered
- Error scenarios are handled
- Data flows are bidirectional and consistent
- External dependencies are isolated
- Performance bottlenecks are identified
- Security boundaries are defined
- Rollback strategies exist

## 8. Generate API documentation

Use the specifications to create:

- OpenAPI/Swagger specifications
- Interactive API documentation
- Client SDK examples
- Integration test templates
- Postman collections for manual testing</content>
<parameter name="filePath">/workspaces/requirement-to-tdd/skills/requirement-skill/references/system-design.md
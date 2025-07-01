# Awesome Cooking Recipes for LLMs [![Awesome](https://awesome.re/badge.svg)](https://awesome.re)

## Reimbursement Agent Repository Issues

### Issue #7: Roadmap details
**Status:** Open  
**Labels:** None  
**Priority:** High  

**Tasks:**
- [ ] Launch AWS feature
- [ ] Increase pricing by 30% to 30$ pu pm
- [ ] Launch alternate product line for debt collection
- [ ] Sales db updates for Q3

---

### Issue #6: Add unit tests and integration tests
**Status:** Open  
**Labels:** testing, quality  
**Priority:** High  

The project currently lacks any testing infrastructure, which is critical for maintaining code quality and preventing regressions.

**Testing Gaps:**
- No unit tests for core functions
- No integration tests for API endpoints
- No tests for Composio integration
- No frontend tests

**Tasks:**
- [ ] Set up pytest for backend testing
- [ ] Add unit tests for email processing logic
- [ ] Add API endpoint tests
- [ ] Mock Composio/Gmail/Sheets APIs for testing
- [ ] Add frontend testing with Jest/React Testing Library
- [ ] Set up CI/CD pipeline with automated testing
- [ ] Add test coverage reporting
- [ ] Create test data fixtures

**Files to Test:**
- `backend/main.py` - API endpoints
- `backend/core/agent_logic.py` - Email processing logic
- `backend/core/composio_tools.py` - Composio integration
- Frontend components and API integration

---

### Issue #5: Improve error handling and user feedback
**Status:** Open  
**Labels:** bug, enhancement  
**Priority:** High  

The current error handling could be more robust and provide better feedback to users.

**Areas for Improvement:**
1. **Connection Error Handling**: Better error messages when Gmail/Sheets connections fail
2. **Validation**: Input validation for email queries and sheet URLs
3. **Rate Limiting**: Handle API rate limits gracefully
4. **User-Friendly Errors**: Convert technical errors to user-friendly messages

**Tasks:**
- [ ] Create custom exception classes for different error types
- [ ] Add input validation with clear error messages
- [ ] Implement retry logic for transient failures
- [ ] Add proper error codes and messages
- [ ] Create error handling middleware
- [ ] Add monitoring/alerting for critical errors

---

### Issue #4: Add comprehensive API documentation
**Status:** Open  
**Labels:** documentation  
**Priority:** Medium  

The API needs better documentation for both developers and users of the service.

**Missing Documentation:**
- [ ] API endpoint documentation (beyond basic FastAPI auto-docs)
- [ ] Authentication flow documentation
- [ ] Setup and deployment guide
- [ ] Environment variables documentation
- [ ] Error code reference
- [ ] Example requests/responses
- [ ] Integration guide for Composio/Gmail/Sheets

**Tasks:**
- [ ] Create comprehensive README.md at root level
- [ ] Add OpenAPI/Swagger documentation enhancements
- [ ] Create developer setup guide
- [ ] Document the Gmail query processing flow
- [ ] Add troubleshooting guide
- [ ] Create API usage examples

---

### Issue #3: Implement proper logging system
**Status:** Open  
**Labels:** enhancement, logging  
**Priority:** Medium  

The application currently uses print statements for logging, which is not suitable for production.

**Current Issues:**
- Using `print()` statements throughout the codebase
- No log levels (DEBUG, INFO, WARNING, ERROR)
- No log formatting or structured logging
- No log rotation or persistence

**Tasks:**
- [ ] Replace print statements with Python logging module
- [ ] Configure different log levels for development vs production
- [ ] Add structured logging with JSON format
- [ ] Implement log rotation
- [ ] Add request ID tracking for better debugging
- [ ] Configure log aggregation for production deployment

---

### Issue #2: Replace hardcoded URLs with environment configuration
**Status:** Open  
**Labels:** enhancement, configuration  
**Priority:** Medium  

The application currently has several hardcoded URLs that should be configurable through environment variables.

**Hardcoded URLs found:**
1. Frontend redirect URLs: `http://localhost:5173/connection-callback`
2. CORS origins: `http://localhost:5173`, `http://127.0.0.1:5173`, `http://localhost:3000`
3. Server host/port configuration

**Tasks:**
- [ ] Add environment variables for frontend URL
- [ ] Make CORS origins configurable
- [ ] Add environment-specific configuration files
- [ ] Update documentation with required environment variables
- [ ] Add validation for required environment variables on startup

---

### Issue #1: Replace placeholder authentication system with proper user authentication
**Status:** Open  
**Labels:** enhancement, security  
**Priority:** High  

Currently, the authentication system is just reading a user ID from the `X-User-ID` header, which is not secure for production use.

**Current Implementation:**
```python
async def get_current_user_entity_id(request: Request) -> str | None:
    user_id = request.headers.get("X-User-ID")
    if user_id:
        # Basic validation/sanitization could be added here
        print(f"Received User ID from header: {user_id}")
        return str(user_id)
    print("Warning: X-User-ID header not found in request.")
    return None
```

**Tasks:**
- [ ] Implement proper JWT-based authentication
- [ ] Add user registration/login endpoints  
- [ ] Integrate with OAuth providers (Google, etc.)
- [ ] Add proper session management
- [ ] Update frontend to handle authentication flow
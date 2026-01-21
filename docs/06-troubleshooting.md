# Troubleshooting Notes

## net::ERR_NAME_NOT_RESOLVED

Cause: Incorrect API URL, extra spaces, `%20` in request.
Fix: Use relative `/api/...` in Angular and route internally via Nginx reverse proxy.

## CORS Issues

Final fix is architectural:

- Backend is ClusterIP (internal)
- Only frontend is public
- Browser never calls backend directly
- Nginx proxies `/api/*` to backend service internally

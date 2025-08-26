# Angular Services

This will contain all services used within the framework for data that needs to be communicated
across components that shouldn't be part of an input or attribute of sorts.

## Auth Service

This service is responsible for checking the state of the user via `GET /api/auth/status`.
If the user is unauthenticated, return false for `isAuthenticated()`.
If they are, they get access to protected components.

The data structure coming back from the server should look like this:

```json
{
  "authenticated": true|false,
  "expiry": "2000-01-01T00:00:00Z", // ISO timestamp for when this session expires and should be deleted from the browser.
  "user": {/*user datagram structure will detail user details here*/},
}
```

On first page load/service constructor, the service should ask the server for the authentication
status of the user. This should contain a way for other components to subscribe to the auth state
changing.

The login page will invoke a change to this service to indicate the user has changed auth states if
they logged in successfully. The logout page will indicate to this service the user has logged out.
So include a function that will update if the state changes.

No other methods are needed for this service as calling methods/components will handle that objective.

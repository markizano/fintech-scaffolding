# Kizano's FinTech: Application

This is the application root.

Please make sure to provide the HttpClient here for other components to leverage.

Navigation must be included in the application at all times.

Please ensure routes are setup accordingly.

These are page components that don't require authentication. User can visit them freely.
Match the following route list:

- /: Home Page Component
- /auth/login: Login Form Component
- /auth/logout: Logout session clearing Component
- /auth/register: Account Registration Form Component
- /auth/forgot: Forgot Password Form Component
- /auth/recover: Account Recovery Form Component
- /privacy: Privacy Policy Component
- /tos: Terms of Service Component

These pages require authentication. Ensure they are protected with AuthGuard.
Match the following route list in addition to the above list:

- /auth/profile: Ability to edit and update user profile and preferences.
- /schedule: Schedule time Component
- /attend: Sign up to attend a class event
- /lectures: Class history and lecture list Component
- /lectures/:id: Lecture Detail Component

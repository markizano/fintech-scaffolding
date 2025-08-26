---
alwaysApply: false
autoAttached: true
globs: **/auth/*
description: Pages related to authentication and profile management.
---

# Authentication Module

All things related to authentication go here.

**Avoid using deprecated code!!!** - Use Angular-v20 modern testing mechanisms.
**Avoid hallucinating colors!** - Refernce @src/styles.css for the full color palette.
Avoid setting `min-height: 100vh` for form component wrappers.

Please reference @AGENTS.md in the root of the project for coding standards and project
specifications.
Reference global settings to ensure you are honouring code compliance.

## Login Component

User can authenticate here using username and password.

Request is sent via `POST /api/auth/login` with the username and password in the form fields.

A "remember me" textbox stores the user's username in the `sessionStorage` of the browser.
The username text field should check this if its been stored previously.
Upon submitting the form, the username is saved to the browser's session.

If the server sends back success: Notify the change of state in the auth service.

If the server sends back error: Indicate as such on the login page as to why.

Be sure to include register and forgot password links alongside the form so the user can get their
access as needed.

The password field should be the custom password field in `utils/password-field`.

### Testing Login

**Remember to AVOID USING DEPRECATED CODE!!!** - Use Angular-v20 modern testing mechanisms.

To test the login page, let's assert at least the following:

- Username is required.
- Password is required.
- Any form errors should render upon invalid input.
- A successful login should update the `localStorage` with the session object returned by the server.
- A failure login should render the error from the server.
- Any other relevant tests you can think of that a login page should have.

## Logout Component

Clears the `localStorage` in the browser and sends a simple `GET /api/auth/logout` so the server
can clear the session from the server as well.

Upon a successful logout, return the user to the homepage. There's no need to wait for a response
from the server, fire and forget, but make sure it is at least received by the server before
navigating away to avoid a 499 from the server.

### Testing Logout

**Remember to AVOID USING DEPRECATED CODE!!!** - Use Angular-v20 modern testing mechanisms.

To test the logout page, let's at least assert the following:

- Upon reaching this page, it should send a `GET /api/auth/logout` to the server.
- It should clear the browser's `localStorage`.
- It should redirect to the home page after clearing the session and notifying the server.

## Forgot Password

This is available from the login screen. The user should be able to submit their email and send
that in a `POST /api/auth/forgot`. If successful, the server will
generate a random code and send the user an email with instructions to reset their password.

After submission, thank the user, inform them of the potential email and that it will come from
`no-reply@markizano.net`, they should whitelist that address, & check their spam and promotional
inboxes.

Email is the only required input field here.

### Testing Forgot Password

**Remember to AVOID USING DEPRECATED CODE!!!** - Use Angular-v20 modern testing mechanisms.

To test the forgot password page, we should assert at least the following:

- Email is required.
- It should render errors if email is not provided and disable submission of the form.
- It should send a `POST /api/auth/forgot` with `{"email": "$email"}` in the payload as JSON.
- It should render an error if the server responds with an error.
- It should render a generic response if the form was accepted by the server.

## Recover Account

Once the user has clicked on the "reset password" link, they would be sent to this page.

On this page, it should take in the account recovery code along with the new password credentials
and send a `POST /api/auth/recover` to attempt to reset the account.

If the server kicks back an error, indicate as such to the user.

If the URL is missing `code=` in the GET params, it should render an error instead of the password
reset form. Use Angular methods of checking for the code, do not do a string match against the
query string. If the code is missing or empty, don't even render the password reset form. Display
an error indicating they need to click the link in the email.

The password field should be the custom password field in `utils/password-field`.

### Testing Recover Account

**Remember to AVOID USING DEPRECATED CODE!!!** - Use Angular-v20 modern testing mechanisms.

To test the account recovery form, we should assert at least the following:

- If the GET param `code` is missing from the URL, render an error instead of the form.
- Password and verify are required and password must match.
- It should render errors if the form is invalid.
- It should send a `POST /api/auth/recover` with the code and password in the payload as JSON.
- It should render an error if the server responds with an error.
- It should redirect the user to the login screen after successful reset of the password.

## Sign Up

For the account registration page, there's very simple data to collect to register a user account.
All fields are required unless they have a trailing asterisk(*).

- First Name
- Last Name
- eMail
- Current Title*
- Future Title*
- How can I best help you in your journey?*
- Username
- Password
- Verify Password
- Agree to the TOS and Privacy Policy

For the "How can I best help you" field, this is an open resizable textarea where the user can include up to
5000 characters.

The password field should be the custom password field in `utils/password-field`.

Only password requirement is at least 12 characters. No other complexity requirements.

The form should be submitted to `POST /api/auth/register`.
If there are issues, it should render the errors on the screen.

### Testing Account Registration

**Remember to AVOID USING DEPRECATED CODE!!!** - Use Angular-v20 modern testing mechanisms.

To test the account registration, we should at least test the following:

- All required fields should be provided.
- Any form errors should render a descriptive actionable response for the user.
- It should send a `POST /api/auth/signup` with the form details in a JSON payload. Empty fields should be empty, not omitted.
- If the server kicks back an error, it should render the error for the user.
- If the form is successful, it should redirect to the login screen.

## Profile

For the profile section, the user can change their information and set preferences.

Everything from the registration would be available here. Let's create a read-only version where they
can just view the details, and an editable version once they click an "edit" button that swaps the
display of information with a form that intakes the information for update.

For updating the user profile, it should `POST /api/auth/profile`.

The password field should be the custom password field in `utils/password-field`.

### Testing Profile Page

**Remember to AVOID USING DEPRECATED CODE!!!** - Use Angular-v20 modern testing mechanisms.

To ensure the profile page works as expected, we should assert at least the following:

- When not editing, it should render the profile details.
- When editing, it should render a form for updating profile information.
- If there are any problems with the form, it should render appropriate errors.
- It should send a `POST /api/auth/profile` to update the profile details.
- If the server kicks back an error, it should render the error for the user to fix.
- If the server is successful in updating the user's information, it should immediately update the displayed details and give a fading confirmation.

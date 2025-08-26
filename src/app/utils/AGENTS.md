# Utility Components

These components are used more for utility than rendering pages. These are included in other
standalone components to bring a more rich experience.

## Navigation Bar

This is responsible for enabling the user to navigate the site. Contains links to allow changing
the rendered page.

This component should only render links to which the user has access depending on if they are
logged in or not. As described in the routes, if the user is not authenticated, they should
be shown buttons to enable them to login, register, forgot password.

If authenticated, the user should be shown the schedule, attend, lectures, profile and logout
buttons.

## Password Field

No work is necessary on this component. This one of the few things copied from another project
that is "plug & play" available without any extra work. It's a custom password field that
enables making the password visible or hidden depending on user preference.

This was implemented due to limitations in Angular Material's similar password textbox
implementation.

## Cal.com Integration

This is another copy-paste component from another project that renders the cal.com integration.
Simply include this where needed. No additional work required in order to make this component
work.

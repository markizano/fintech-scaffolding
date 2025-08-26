# Schedule a Coaching Session

This page allows the user to schedule 1:1 coaching time with me.

It simply renders the `cal.com` component.

## Cal.com details

When rendering the cal.com widget, be sure to:

- Set the `config.layout = "week_view"`.
- Set the `config.firstName` and `config.lastName` and `config.email` as per what is in the user object.
- Set the `calLink` to `kizanos.fintech/${eventType}`

For now, just stub the `eventType` to "coaching-15". There will be more meeting types later depending
on the user's role, but I'm not yet ready to implement RBAC just yet. So keep the code forward-looking.

Just like the attendance page component, it should render the `cal.com` component for the user to
select their time and the plugin will render the confirmation page when done and email the user.

Please emphasis on the fact that this time is for the user to find the best growth in their
journey. They are encouraged to have an agenda or some kind of direction to take with the session
to receive the most benefit from what I can offer.

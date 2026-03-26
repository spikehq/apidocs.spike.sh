---
description: >-
  Welcome to Spike's API to programmatically manage incidents and on-call
  schedules.
---

# Getting started

Spike’s API lets you programmatically manage incidents, teams, users, on-call schedules, and more.

You can use the API to integrate Spike with your systems, automate workflows, or build custom tooling around incident response.



Most API requests require:

* an API key for authentication
* a team **`_id`** to scope the request

Your typical flow will look like this:

1. Generate your API key from the Spike dashboard ([_find it here_](https://app.spike.sh/api))
2. Fetch your teams using the API ([_learn more_](https://docs.spike.sh/spike-api-docs/teams#get-teams-get-all-teams))
3. Use the team ID in subsequent requests

The API is REST-based and returns JSON responses.

***

### Base URL

```
https://api.spike.sh
```

All API requests should be made to this base URL.

***

### Authentication

Spike API uses API key authentication.

Include your API key in every request using the header below:

```
x-api-key: YOUR_API_KEY
```

You can generate your API key from: [https://app.spike.sh/api](https://app.spike.sh/api)

{% hint style="info" %}
The API key has full access to your organization’s API capabilities. Granular permissions (read-only, write-only, etc.) are not supported at the moment.
{% endhint %}

***

### Team context

Many Spike API endpoints are scoped to a team.

For these requests, you must include the team **`_id`** in the header:

```
x-team-id: TEAM_ID
```

#### How to get your team ID

[Call the Teams endpoint](/broken/pages/188c899c9509971dbc2f06882c5ca4843d6c6837)

```
GET /teams
```

Example:

```
curl -X GET https://api.spike.sh/teams \
  -H "x-api-key: YOUR_API_KEY"
```

From the response, copy the **`_id`** of the team you want to use.

***

### Example request

```
curl -X GET https://api.spike.sh/incidents \
  -H "x-api-key: YOUR_API_KEY" \
  -H "x-team-id: TEAM_ID"
```

This will return a list of incidents for the given team.

***

### Notes

You can download the complete OpenAPI specification directly from this documentation.

Most API routes require a `x-team-id` header. Spike operates with team-scoped data — incidents, integrations, escalation policies, and alert routing rules belong to a specific team.\
Because of this, requests are handled one team at a time. You cannot query or operate across multiple teams in a single request.

***

### Try it out

This documentation is interactive.

You can test API endpoints directly by clicking the **“Test it”** button on any route and providing your API key and team ID.

***

### Feedback

We’re actively improving the API and adding more capabilities.

If you have feedback, questions, or run into issues, reach out to us via the chat widget in the bottom-right corner.

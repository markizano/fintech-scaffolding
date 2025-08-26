---
alwaysApply: false
globs: **/lectures/*
description: Lectures and classes pages.
---

# Lectures List Page

Lectures will be listed here. You can make a `GET /lectures.json` and that will contain the list of
videos to render. It's a static JSON file packaged with the application. No server required.

Please see @../../../../public/lectures.json for the structure of the JSON. This is generated
from @../../../../bin/videos.py.

Each lecture should render as a card with a video preview thumbnail with a title and description.
Clicking on a lecture will navigate to `/lectures/:id` where the lecture detail page will render
the content available and full details.

Lectures should be grouped by the category as described by the JSON structure.
Groups should be expandable and collapsible for ease of viewing.

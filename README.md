# React Router Dom v6 Catch All Route Issue

This repository demonstrates a common issue encountered when using the catch-all route (`/*`) in React Router v6. The problem arises when a catch-all route is placed alongside more specific routes where some of the specific routes' paths are substrings of others. In such a scenario, navigation to a route that is a substring of another route can lead to unexpected behavior. The catch-all route will prematurely capture the request, preventing the correct route from being rendered.

## How to Reproduce

1. Clone this repository.
2. Run `npm install`.
3. Run `npm start`.
4. Observe the behavior when navigating between routes.  You'll see that if you navigate to `/about`, which is a substring of `/about/something`, the `NotFound` component will be rendered incorrectly, rather than `/about`.

## Solution

The issue lies in the order of routes defined.  React Router processes routes sequentially, and the catch-all route will interfere with correctly resolving nested routes or routes that are substrings of each other.  To fix this, place catch-all routes at the end of your routes configuration.

This bug occurs due to the way React Router matches routes. The catch-all route is too broad in this instance and will prevent the correct route from rendering in certain cases, depending on the defined routes. 
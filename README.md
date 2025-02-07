# Silent Failure on Non-JSON Response in React Fetch

This example demonstrates a common error in React applications where fetching data doesn't explicitly check for non-JSON responses, leading to a silent failure. The component appears to work fine, but no data is rendered because `response.json()` throws an error when the response isn't valid JSON.

## Bug

The `bug.js` file contains the buggy code.  It fetches data, but it only handles HTTP errors, it doesn't check the response's content-type to make sure it is actually JSON. If the server sends back a non-JSON response, an error is thrown silently, leaving the component in an error state with no indication of the problem. 

## Solution

The solution is provided in `bugSolution.js`. It correctly handles this case by checking the `response.ok` property (to ensure the request succeeded) and the `response.headers.get('content-type')` to make sure that the response is actually JSON before attempting to parse it with `response.json()`.  Appropriate error handling is also in place. 
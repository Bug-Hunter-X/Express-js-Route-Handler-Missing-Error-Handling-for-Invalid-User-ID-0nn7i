# Express.js Route Handler Missing Error Handling for Invalid User ID

This repository demonstrates a common error in Express.js route handlers: the lack of proper error handling for invalid input.  Specifically, this example shows a route that fetches a user by ID, but fails to handle the case where the ID is not a valid integer. This can lead to unexpected behavior or crashes.

## Bug

The `bug.js` file contains the faulty code. It attempts to parse the user ID as an integer without checking for errors. If the ID is not an integer, `parseInt` will return `NaN`, and the subsequent comparison will always fail, resulting in a 404 error even if a user with that ID exists, or it may throw an exception in other scenarios.  This is a subtle error that can be difficult to debug.

## Solution

The `bugSolution.js` file demonstrates the corrected code.  It includes explicit checks to ensure the user ID is a valid integer before attempting to access the user object.  It uses `isNaN` to check if the conversion resulted in a number. If the ID is invalid, it returns a 400 Bad Request response.  This approach handles errors gracefully and provides informative feedback to the client.
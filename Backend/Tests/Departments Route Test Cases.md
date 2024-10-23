# Departments Route Test Cases

This section outlines the test cases designed to verify the functionality of the `/departments` and `/department` routes in the Flask application.

## Test Cases

### 1. `test_departments_route`

Description: Tests the /departments route for a valid GET request.
Expectations: The response should return a status code of 200, and the returned departments should match predefined department names and descriptions.

### 2. `test_department_route`

Description: Tests the /department route with a valid department name ("Computer Science").
Expectations: The response should return a status code of 200 and verify that the department's name, description, school ID, professors, and opportunities match expected values.

### 3. `test_department_no_json_route`

Description: Tests the /department route without any JSON input.
Expectations: The response should return a status code of 400, indicating a bad request due to the missing input.

### 4. `test_department_route_incorrect_json`

Description: Tests the /department route with incorrect JSON input.
Expectations: The response should return a status code of 400, indicating a bad request due to invalid input format.



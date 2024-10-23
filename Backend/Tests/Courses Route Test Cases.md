# Courses Route Test Cases

This section outlines the test cases designed to verify the functionality of the `/courses` route in the Flask application.

## Test Cases

### 1. `test_courses_route_with_input_name`

Description: Tests the /courses route with a valid input name ("data").
Expectations: The response should return a status code of 200 and confirm that the first course's code is "CSCI4390" and its name is "Data Mining".

### 2. `test_courses_route_with_input_code`

Description: Tests the /courses route with a valid input code ("cs").
Expectations: The response should have a status code of 200 and verify that the returned courses match a predefined list of course codes and names.

## 3. `test_courses_route_no_json`
Description: Tests the /courses route without any JSON input.
Expectations: The response should return a status code of 400, indicating a bad request due to the missing input.

### 4. `test_courses_route_incorrect_json`
Description: Tests the /courses route with incorrect JSON input.
Expectations: The response should return a status code of 400, indicating a bad request due to invalid input format.

### 5. `test_courses_not_found`
Description: Tests the /courses route with an input that does not match any existing courses ("not found").
Expectations: The response should return a status code of 404, indicating that the requested resource was not found.
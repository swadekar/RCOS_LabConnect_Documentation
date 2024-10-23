# Test Code Documentation

The following test code uses `pytest` to create a set of fixtures for testing the Flask application named `labconnect`. These fixtures help set up the necessary context and data for testing various functionalities of the application.

## Overview of Fixtures

Fixtures are a way to set up a testing environment. They can provide context and data that tests can use, and they can be scoped to either the entire test module or individual tests.

### 1. `test_client` Fixture

```python
@pytest.fixture(scope="module")
def test_client():
    # Set the Testing configuration prior to creating the Flask application
    flask_app = create_app()
    flask_app.config.update({"TESTING": True, "DEBUG": True})

    # Create a test client using the Flask application configured for testing
    with flask_app.test_client() as testing_client:
        # Establish an application context
        with flask_app.app_context():
            yield testing_client  # this is where the testing happens!

Purpose: This fixture sets up a test client that can be used to simulate requests to the Flask application.
Configuration: The Flask application is configured with TESTING and DEBUG set to True, which enables testing features and debugging.
Usage: The testing_client is yielded to the tests, allowing them to send requests to the application as if they were actual clients.
2. Commented Out Fixtures
The following fixtures are commented out in the provided code. They are essential for initializing the database and handling user logins.

2.1 init_database Fixture

# @pytest.fixture(scope="module")
# def init_database(test_client):
#     # Create the database and the database table
#     db.create_all()
#     ...
#     yield  # this is where the testing happens!
#     db.drop_all()

Purpose: This fixture initializes the database by creating the necessary tables and inserting test data.
Data Insertion: It adds default users and books to the database.
Yielding: The fixture yields control back to the tests after the setup, allowing them to interact with the initialized database.
Cleanup: After the tests complete, it drops all tables to clean up the test database.

2.2 log_in_default_user Fixture
# @pytest.fixture(scope="function")
# def log_in_default_user(test_client):
#     test_client.post(
#         "/login", data={"email": "patkennedy79@gmail.com", "password": "FlaskIsAwesome"}
#     )
#     yield  # this is where the testing happens!
#     test_client.get("/logout")

Purpose: This fixture logs in the default user before each test that requires an authenticated user.
Login Process: It sends a POST request to the /login route with the user's credentials.
Yielding: Control is yielded to the tests, allowing them to run while the user is logged in.
Logout: After the tests complete, it logs the user out.

2.3 log_in_second_user Fixture
# @pytest.fixture(scope="function")
# def log_in_second_user(test_client):
#     test_client.post(
#         "login", data={"email": "patrick@yahoo.com", "password": "FlaskIsTheBest987"}
#     )
#     yield  # this is where the testing happens!
#     test_client.get("/logout")

Purpose: Similar to the log_in_default_user fixture, this one logs in a second user for testing.
Usage: It enables tests to run as if the second user is logged in, allowing for testing user-specific functionalities.
Logout: It also logs out the user after the tests are completed.
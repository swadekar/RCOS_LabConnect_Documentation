# Department Route Implementation

## Current Code
The current implementation for the department route in the application is as follows:

```python
@main_blueprint.route("/department/<string:department>")
def department(department: str):
    return render_template("department.html")

Department and School Overview
Each department is associated with a specific school, allowing professors to post projects that can reach a broader audience of students. This functionality enables the following:

Schools and Associated Departments
ITWS
Lally
School of Architecture
School of Engineering
HASS
School of Science
Professors have the option to post projects at the school level, which widens the pool of potential student participants.

Specific Departments/Majors within a School
Computer Science
Other Majors (e.g., ECT)
Professors can also choose to target specific majors when posting projects, enabling them to connect with students who meet particular criteria.

User Interface for Students
Students will be able to navigate through the interface by selecting schools and then drilling down to specific majors. The following structure will be used:

Department Variables
School
Department
Department Table Example
Department
ITWS
Lally
School of Architecture
School of Engineering
HASS
School of Science
Implementation Requirements
To fully implement this functionality, the following steps should be taken:

Query for Schools and Departments: Implement a query that retrieves the list of schools and their associated departments.
Fetch Past Projects: Query the database to gather past projects associated with each professor.
Return Data in JSON Format: Structure the returned data in JSON format to facilitate easy consumption by the front-end.
Expected Data Return Format
The expected JSON structure for the returned data should be as follows:

{
  "professors": [],
  "projects": []
}
Current Functionality
As it stands, the current implementation returns the following data:

Department (School)
Description
Major







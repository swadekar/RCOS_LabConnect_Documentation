# Profile Page Implementation

## Overview
The Profile Page will display the user's name, major/department, class level, and their past opportunities.

## Data Needed
The following data is required for the profile:

### Profile Variables
- **Username**: `string`
- **Title/Level**: `string`
- **Department**: `string`

### Projects
#### Current Opportunities:
- **Professor**: `string`
- **Credits**: `int`
- **Description**: `string`

#### Past Opportunities:
- **Professor**: `string`
- **Credits**: `int`
- **Description**: `string`

## Objectives
To implement this functionality, the following steps should be completed:

1. **Query the Users Database**: Access the user information and retrieve the necessary data from the User object.
2. **Access Current and Previous Projects**: Query the opportunities database to obtain the user's current and past projects.

## Output JSON Data Format
The expected JSON structure for the profile data should be as follows:

```json
{
  "Profile": {
    "rcs_id": "str",
    "name": "str",
    "email": "str",
    "phone_number": "123-456-7890",
    "website": "str",
    "title": "str",
    "departments": "str",
    "past_opportunities": [
      {
        "professor": "str",
        "credits": int,
        "description": "str"
      }
    ],
    "current_opportunities": [
      {
        "professor": "str",
        "credits": int,
        "description": "str"
      }
    ]
  }
}

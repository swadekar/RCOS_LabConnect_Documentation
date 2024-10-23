# Labconnect's Discover Page

The Discover Page on Labconnect is a key feature designed to help students find research opportunities tailored to their needs and interests. When a user accesses Labconnect, the Discover Page automatically opens, displaying a list of suggested research opportunities based on an algorithm.

## How the Algorithm Works
Currently, the algorithm prioritizes opportunities based on two main criteria:

1. **Relevance to the User’s Major**: Research opportunities that align with the user's declared major are prioritized.
2. **Recency**: Newly posted opportunities are given higher priority.

The opportunities are ranked according to their score in the algorithm, and a limited number of suggestions will be displayed at any given time. Future updates to the algorithm may be implemented to improve the accuracy of suggestions.

## Opportunity Previews
Each research opportunity will be presented as a preview on the Discover Page, showcasing key details to give students an overview. The following information will be included for each opportunity:

- **Research Opportunity Name**
- **Required/Preferred Major(s)** (space permitting)
- **Required/Preferred Experience** (space permitting)
- **Brief Description** (with truncated text)
- **Credits Offered**
- **Pay Offered**

In addition to these fields, the time each research opportunity was posted will be available, ensuring users can see the most recent opportunities first.

## Data Handling
Research opportunities are stored as class objects, meaning we can query each object's attributes to retrieve the necessary information. This data will be used to both run the algorithm and display the research opportunities on the Discover Page.

## JSON Data Format
We will provide the research opportunities in JSON format, with each entry containing the following fields:

```json
{
  "name": "Research Opportunity Name",
  "major": "Relevant Major(s)",
  "experience": "Required Experience",
  "description": "Brief Description",
  "credits": 3,
  "pay": 1000.00
}

{
  "data": [
    {
      "name": "Research Opportunity 1",
      "major": "Computer Science",
      "experience": "2+ years of coding experience",
      "description": "This research focuses on AI and machine learning...",
      "credits": 3,
      "pay": 1500.00
    },
    {
      "name": "Research Opportunity 2",
      "major": "Biology",
      "experience": "Laboratory work experience preferred",
      "description": "Research on genome editing technologies...",
      "credits": 4,
      "pay": 1200.00
    }
  ]
}

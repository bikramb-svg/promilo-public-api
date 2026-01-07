s.

# API Use Cases

This document describes common, real-world ways the **Promilo Public API** is used to discover courses and institutions.

The API is currently **course-centric** and keyword-driven. Most applications combine API search with client-side filtering to build meaningful discovery flows.

---

## 1. Finding BCA colleges in Kolkata

### Scenario
A student has completed 12th with mathematics and is looking for **BCA colleges in Kolkata**.  
Instead of browsing multiple college websites, they want a single structured list of relevant course offerings.

Since the API returns course data, the typical approach is to search by keyword and then filter results by location.

---

### Sample request (curl)

```bash
curl -X GET "https://api.promilo.com/courses?keyword=BCA&page_number=0"

Sample response (simplified)
{
  "count": 1,
  "courses": [
    {
      "campaignId": "8a81808699e1e8b70199f0e54553304b",
      "description": "Bachelor of Computer Applications program focused on software fundamentals.",
      "deliveryMode": "Regular / Offline",
      "collegeName": "Techno International New Town",
      "stream": "Computer Applications",
      "subStream": "BCA",
      "location": "Kolkata",
      "collegeFees": "3.20 Lakhs",
      "courseDuration": "3 YEAR",
      "courseUrl": "https://www.promilo.com/course/bca-tint"
    }
  ]
}

How this is typically used

Filter courses[] by location containing Kolkata

Group results by collegeName

Build pages like:

BCA colleges in Kolkata

Top BCA courses in West Bengal

Power counsellor dashboards and AI chat assistants

2. Exploring MBA programs by keyword
Scenario

A working professional wants to explore MBA programs without fixing a city upfront.
They start with keyword-based discovery and then compare colleges, fees, and locations.

Sample request (curl)
curl -X GET "https://api.promilo.com/courses?keyword=MBA&page_number=0"

Sample response (simplified)
{
  "count": 1,
  "courses": [
    {
      "campaignId": "9b72808688e1e8b70188f0e54553399a",
      "description": "MBA program with specialisation in Marketing and Finance.",
      "deliveryMode": "Regular / Offline",
      "collegeName": "Institute of Public Enterprise",
      "stream": "Management",
      "subStream": "MBA",
      "location": "Hyderabad",
      "collegeFees": "8.50 Lakhs",
      "courseDuration": "2 YEAR",
      "courseUrl": "https://www.promilo.com/course/mba-ipe"
    }
  ]
}

How this is typically used

Compare MBA programs across multiple cities

Display realistic fee ranges using collegeFees

Feed admission advisory tools and recommendation systems

Answer questions like “Which MBA options fit my budget?”

3. Using accreditations, rankings, and entrance exams for decisions
Scenario

A student has shortlisted a course and wants deeper clarity before applying:

Is the college accredited?

Are entrance exams required?

Does it appear in rankings?

This information is already embedded in the course response.

Sample request (curl)
curl -X GET "https://api.promilo.com/courses?keyword=B.Tech&page_number=0"

Sample response (focused fields)
{
  "count": 1,
  "courses": [
    {
      "collegeName": "BMS College of Engineering",
      "subStream": "B.E. / B.Tech",
      "location": "Bengaluru/Bangalore",
      "entranceExams": [
        {
          "label": "KCET",
          "value": "kcet",
          "cutoff": "General - 85"
        }
      ],
      "accreditation": [
        {
          "label": "NAAC",
          "value": "A+"
        }
      ],
      "rankings": [
        {
          "label": "NIRF",
          "ranking": 98
        }
      ]
    }
  ]
}

How this is typically used

Course detail and comparison pages

Admission decision dashboards

AI assistants answering questions like:

“Is this college recognised?”

“Which exams do I need to prepare for?”

Notes on API usage

The API is keyword-first, not filter-heavy

Most filtering (city, stream grouping, comparisons) is handled on the client side

This keeps the API flexible and adaptable across different products

More use cases will be added as the API evolves.

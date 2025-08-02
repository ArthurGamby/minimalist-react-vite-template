```markdown
# Hacker News Job Board

Build a job board that displays the latest job postings fetched from the Hacker News API, with each posting displaying the job title, poster, and date posted.

---

## Requirements

1. The page should show **6 jobs** on initial load with a button to **load more** postings.
2. Clicking the **Load more** button will load the next page of 6 postings.
   - The button does **not** appear if there aren’t any more postings to load.
3. If a `url` field is returned for the job details, make the **job title** a link that opens the job details page in a new window when clicked.
4. The timestamp can be formatted in any way you like.

---

## API

Hacker News has a public API to fetch jobs by Y Combinator companies.  
There’s no single endpoint that returns both the list of job IDs and their details in one call—you must fetch them separately and combine the results.

### Job Stories

- **Purpose**: Fetches a list of job posting IDs.
- **URL**
```

- **Method**: GET
- **Response**: JSON array of IDs
- **Sample response**:

```json
https://hacker-news.firebaseio.com/v0/jobstories.json


[35908337, 35904973, 35900922, 35893439, 35890114, 35880345, ...]

```

### Job Details

- **Purpose**: Fetches job posting details given its ID.
- **URL**

  ```
  https://hacker-news.firebaseio.com/v0/item/{id}.json
  ```

- **Method**: GET
- **Response**: JSON object with job properties
- **Sample request**:
  `https://hacker-news.firebaseio.com/v0/item/35908337.json`
- **Sample response**:

  ```json
  {
    "by": "jamilbk",
    "id": 35908337,
    "score": 1,
    "time": 1683838872,
    "title": "Firezone (YC W22) is hiring Elixir and Rust engineers",
    "type": "job",
    "url": "https://www.ycombinator.com/companies/firezone/jobs"
  }
  ```

---

## Notes

- The focus of this exercise is on **functionality**, not styling—feel free to add minimal, clean styles if you like.
- To improve user experience and avoid over-fetching, you may limit the number of job-details requests to exactly the number of jobs currently visible on the page.

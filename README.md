# Quick-Guide-SkillFinder

This guide provides instructions on how to use the SkillFinder API, which allows you to search for relevant skill data.

## Using the SkillFinder API

### Endpoint

- URL: `https://find.skilldata.info/send_query_full`
- Method: POST

### Request Structure

#### Headers

- `Content-Type`: application/json
- `KIC-API-HEADER`: Your API key

#### Body (JSON)

```json
{
  "skill_input": "YOUR_SEARCH_QUERY",
  "language": "en"
}
```

- `skill_input`: Your search query
- `language`: 2-character language code (ISO 639-1)

### Response

The API returns relevant skill data based on your search query. The response is limited to 12 records.

### Implementation Examples

#### Python

```python
import requests

url = "https://find.skilldata.info/send_query_full"

headers = {
    "Content-Type": "application/json",
    "KIC-API-HEADER": "YOUR_API_KEY"  # Replace with your actual API key
}

data = {
    "skill_input": "Data Science",
    "language": "en"
}

response = requests.post(url, json=data, headers=headers)
print(response.json())
```

#### JavaScript

```javascript
const url = "https://find.skilldata.info/send_query_full";

const headers = {
  "Content-Type": "application/json",
  "KIC-API-HEADER": "YOUR_API_KEY"  // Replace with your actual API key
};

const data = {
  skill_input: "Data Science",
  language: "en"
};

fetch(url, {
  method: "POST",
  headers: headers,
  body: JSON.stringify(data)
})
  .then(response => response.json())
  .then(data => {
    console.log('Success:', data);
  })
  .catch(error => {
    console.error('Error:', error);
  });
```

## Technical Details

- The API uses vector search, utilizing embeddings from OpenAI.
- The search is performed on a self-hosted PostgreSQL database with the pgvector extension.
- The response is limited to 12 records per query.

## Note

Remember to replace `"YOUR_API_KEY"` with your actual API key in the examples above.
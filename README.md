# kibana-Dashboard-using-ELK-Stack
![image](https://github.com/user-attachments/assets/2bff2472-7377-407f-8e33-c371215d3022)
![image](https://github.com/user-attachments/assets/3aea4751-6e05-474a-8448-d7a371c5230f)

🧩 Project Title:
Building a Kibana Dashboard with Elasticsearch Queries on Web Logs using ELK Stack

🎯 Objective:
To create a real-time dashboard that visualizes HTTP web traffic patterns from structured log files using the ELK Stack — enabling easy log ingestion, querying, and visualization.

⚙️ Tech Stack:
Elasticsearch: Stores and indexes the structured log data

Logstash: Parses and ingests raw JSON log entries

Kibana: Visualizes the data using interactive dashboards

Docker + Docker Compose: Containerized orchestration of the ELK stack

📂 Dataset:
File: sample_logs.json
Format: NDJSON (JSON Lines)
Fields:

timestamp: ISO8601 datetime

ip: Client IP address

method: HTTP method (GET, POST)

endpoint: Accessed route (e.g., /home, /login)

response: HTTP response code (e.g., 200, 401)

bytes: Size of the response payload

🛠️ Implementation Steps:
1. Environment Setup
A docker-compose.yml file was created to spin up:

Elasticsearch on port 9200

Logstash on port 5044

Kibana on port 5601

2. Logstash Configuration
A logstash.conf file defined:

Input: JSON file from local volume

Filter: Parsed timestamps and structured fields

Output: Sent data to Elasticsearch index named weblogs

3. Data Ingestion
The sample log file (sample_logs.json) was mounted into the container.

Logstash read and parsed the file, pushing the logs into Elasticsearch.

4. Kibana Setup
The weblogs index was discovered and linked using a Data View with timestamp as the time field.

Time range was adjusted to ensure visibility of data.

📊 Visualizations Created in Kibana (using Lens):
Requests Per IP (Bar Chart)

Shows how many times each IP accessed the server.

HTTP Method Usage (Pie Chart)

Visual breakdown of GET vs POST requests.

Traffic Over Time (Line Chart)

Sum of response payload size (bytes) over time to detect traffic spikes.

📋 Dashboard:
A custom Web Logs Dashboard was created in Kibana, combining all visualizations for real-time monitoring. This helps in:

Identifying suspicious IP activity

Analyzing request method usage trends

Monitoring server load over time

🔍 Sample Elasticsearch Query (used in Dev Tools):
json
Copy
Edit
GET weblogs/_search
{
  "query": {
    "match": {
      "endpoint": "/login"
    }
  }
}
✅ Results:
Logs were ingested successfully into Elasticsearch.

All visualizations were functional and dynamically updating with time filtering.

Dashboard provided instant insights into request patterns.

📌 Learnings:
Hands-on experience with setting up and orchestrating ELK stack

Understanding how to structure and format logs for ingestion

Writing log parsing pipelines using Logstash

Building dashboards and time-based analytics in Kibana

📦 Folder Structure:
kotlin
Copy
Edit
elk_project/
├── docker-compose.yml
├── logstash/
│   └── logstash.conf
├── data/
│   └── sample_logs.json
🏁 Conclusion:
This project serves as a foundational use case of using the ELK Stack for log analysis and monitoring. With this setup, organizations can scale log ingestion, visualize large datasets in real-time, and set up alerts or anomaly detection in production environments.

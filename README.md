## Installation

Install pip package:
```
%pip install yandex-query-client --upgrade --quiet
```

### Example: simple select

```
# IAM token to access YandexQuery service
IAM_TOKEN="...."

# Folder ID to work within
PROJECT="my_folder_id"

config = YQHttpClientConfig(IAM_TOKEN, PROJECT)
client = YQHttpClient(config)

# start new query
query_id = client.create_query(query_text="select 777", name="my sample query")

# wait query to succeed
result_set_count = client.wait_query_to_succeed(query_id)

# results with column names, types and values in rows
results = client.get_query_all_result_sets(query_id, result_set_count=result_set_count)
print(f"results={results}")
```

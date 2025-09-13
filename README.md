# Ex.No.6 Development of Python Code Compatible with Multiple AI Tools

## Date: 12-09-2025
## Register no. : 212223220103
# Aim:
Write and implement Python code that integrates with multiple AI tools to automate the task of interacting with APIs, comparing outputs, and generating actionable insights with Multiple AI Tools

# AI Tools Required:
OpenAI API (GPT models) – reasoning, summarization, insights.

Hugging Face Transformers – classification, sentiment, embeddings.

scikit-learn – evaluation metrics (accuracy, precision, recall, etc.).

SentenceTransformers / OpenAI Embeddings – semantic similarity comparison.

Matplotlib / Plotly – visualize and compare results.

# Explanation:
This experiment demonstrates how data can be normalized from multiple formats (CSV, JSON) into a unified structure, which can then be used by multiple AI tools for reasoning, classification, and evaluation.

# Python Code:
```
import csv
import json
import os

def load_data(file_path):
    """
    Load data from a .csv or .json file into a list of dictionaries.
    """
    _, ext = os.path.splitext(file_path)
    ext = ext.lower()

    data = []

    if ext == ".csv":
        with open(file_path, mode="r", encoding="utf-8") as f:
            reader = csv.DictReader(f)
            data = [row for row in reader]

    elif ext == ".json":
        with open(file_path, mode="r", encoding="utf-8") as f:
            data = json.load(f)
            if isinstance(data, dict):
                data = [data]
            elif not isinstance(data, list):
                raise ValueError("JSON file must contain a list or dict at top level.")
    else:
        raise ValueError("Unsupported file format. Only .csv and .json are supported.")

    return data


# --- Step 1: Create sample CSV file ---
csv_filename = "data.csv"
with open(csv_filename, mode="w", newline="", encoding="utf-8") as f:
    writer = csv.writer(f)
    writer.writerow(["id", "name", "age", "city"])
    writer.writerow([1, "Alice", 25, "New York"])
    writer.writerow([2, "Bob", 30, "Los Angeles"])
    writer.writerow([3, "Charlie", 28, "Chicago"])

# --- Step 2: Create sample JSON file ---
json_filename = "data.json"
json_data = [
    {"id": 1, "name": "Alice", "age": 25, "city": "New York"},
    {"id": 2, "name": "Bob", "age": 30, "city": "Los Angeles"},
    {"id": 3, "name": "Charlie", "age": 28, "city": "Chicago"}
]
with open(json_filename, "w", encoding="utf-8") as f:
    json.dump(json_data, f, indent=4)

# --- Step 3: Test the function ---
print("CSV Output:", load_data(csv_filename))
print("JSON Output:", load_data(json_filename))

```

# Sample Output:
<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/9d4db1fe-ffa5-42fe-898a-6f4d067d8983" />



# Result: 
The corresponding Prompt is executed successfully.

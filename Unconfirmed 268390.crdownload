import json
from datetime import datetime

# Converts ISO timestamp to milliseconds
def iso_to_millis(iso_str):
    dt = datetime.strptime(iso_str, "%Y-%m-%dT%H:%M:%SZ")
    return int(dt.timestamp() * 1000)

# Read and convert data-1.json
def read_data_1():
    with open("data-1.json", "r") as file:
        data = json.load(file)
    normalized = []
    for item in data:
        normalized.append({
            "timestamp": iso_to_millis(item["timestamp"]),
            "value": item["value"]
        })
    return normalized

# Read data-2.json as-is
def read_data_2():
    with open("data-2.json", "r") as file:
        data = json.load(file)
    return data

# Merge and sort the datasets
def merge_data():
    data1 = read_data_1()
    data2 = read_data_2()
    combined = data1 + data2
    combined.sort(key=lambda x: x["timestamp"])
    return combined

# Test result against data-result.json
def test_solution():
    merged = merge_data()
    with open("data-result.json", "r") as file:
        expected = json.load(file)

    if merged == expected:
        print("✅ All tests passed! Output matches data-result.json.")
    else:
        print("❌ Test failed. Output does not match data-result.json.")
        print("\nYour Output:\n", json.dumps(merged, indent=2))
        print("\nExpected Output:\n", json.dumps(expected, indent=2))

if __name__ == "__main__":
    test_solution()



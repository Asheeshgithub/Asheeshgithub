@ -0,0 +1,104 @@
# Top 3 F1 Lap Time Processor

This project processes lap times for F1 drivers from a CSV file, calculates average lap times and lowest lap times, and generates a JSON file containing the statistics for the top 3 drivers with the least average lap times and overall lowest time.

## Table of Contents

- [Project Structure](#project-structure)
- [Getting Started](#getting-started)
- [Usage](#usage)
- [Logging](#logging)
- [Tests](#tests)
- [Error Handling](#error-handling)

## Project Structure

```plaintext
.
├── src
│   ├── main
│   │   ├── main.py
│   │   └── utils
│   │       ├── data_reader.py
│   │       ├── laptime_processor.py
│   │       └── result_writer.py
│   └── tests
│       └── test_laptimes.py
└── requirements.txt
```

## Getting Started
Prerequisites
Python 3.x
pip (Python package installer)

## Usage
Installing
# Clone the repository:

```
git clone https://github.com/yourusername/f1-laptime-processor.git
cd f1-laptime-processor/engineering
```

Install the required packages:

```pip install -r requirements.txt```

Prepare the input CSV file named laptimes.csv with the following format:

```
driver,laptime
Lewis Hamilton,85.678
Max Verstappen,86.123
Sebastian Vettel,87.456
Lewis Hamilton,84.987
Max Verstappen,85.678
Sebastian Vettel,86.789
Charles Leclerc,88.123
Charles Leclerc,87.456
Lando Norris,86.456
```

Run the main script:
```
python src/main/main.py
```


The results will be written to top3_laptime_statistics.json in the same directory.

## Logging
Logs are written to logfile.log in the project root directory. The log file includes messages at various levels (DEBUG, INFO, WARNING, ERROR, CRITICAL) to help trace the execution flow and identify issues.

## Tests
Unit tests are provided in src/tests/test_laptimes.py. To run the tests:

```python -m unittest discover src/tests```

## Error Handling
The code includes error handling for the following cases:

* File not found: Raises a FileNotFoundError with a descriptive message.
*  Invalid CSV format: Raises a ValueError if the CSV header is incorrect.
* Malformed rows: Skips rows with incorrect format and logs a warning.
* Invalid lap times: Skips rows with non-numeric or negative lap times and logs a warning.


Example JSON Output
The top3_laptime_statistics.json file will contain data in the following format:
```
{
    "Lewis Hamilton": {
        "average_time": 85.3325,
        "lowest_time": 84.987
    },
    "Max Verstappen": {
        "average_time": 85.9,
        "lowest_time": 85.678
    },
    "Sebastian Vettel": {
        "average_time": 87.1225,
        "lowest_time": 86.789
    }
}
```

This output includes the average lap time and the lowest lap time for each of the top 3 drivers in json.


This Markdown-formatted README provides a structured and detailed overview of your project, including setup instructions, usage guidelines, logging, testing, and error handling information, as well as a license section. This should help users understand how to use and contribute to the project effectively.


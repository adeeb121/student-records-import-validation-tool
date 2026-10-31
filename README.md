# Reliable Student Records Import & Validation Tool

A Python-based command-line application that imports student records from a JSON file, validates each record, handles errors safely, and separates valid records from rejected records.

The project focuses on Python exception handling, JSON processing, data validation, and reliable file operations.

This project is developed as part of **Python Technical Training – Module 7: Exception Handling**.

## Project Overview

The Reliable Student Records Import & Validation Tool is designed to process student records stored in a JSON file.

It checks each record for required fields, correct data types, valid marks, and duplicate student IDs. Valid records are saved to a separate JSON file, while rejected records and their error reasons are stored in a text log.

The application continues processing valid records even if some records contain errors.

## Features

- **Safe File Reading:** Reads student records using `with open()` and handles file-related errors.
- **JSON Parsing:** Loads JSON data using `json.load()` and handles malformed JSON separately.
- **Record Validation:** Checks required fields such as student ID, name, department, and marks.
- **Marks Validation:** Ensures marks contain exactly three numeric values between 0 and 100.
- **Duplicate ID Detection:** Rejects duplicate student IDs without overwriting existing records.
- **Custom Exception:** Uses a custom `StudentRecordError` exception for student-record validation failures.
- **Multiple Exception Handling:** Handles file, JSON, type, value, and validation errors separately.
- **Valid Records Export:** Saves only accepted records to `students_valid.json`.
- **Error Logging:** Stores rejected-record explanations and file/format errors in `import_errors.txt`.
- **Final Summary:** Displays accepted and rejected record counts along with output file paths.

## Technologies Used

- **Programming Language:** Python
- **Modules:**
  - `json` – Reading and writing JSON files.
  - `os` – Optional file and path checks.

**Exception Handling Concepts:**
- `try`
- Multiple `except` blocks
- `else`
- `finally`
- `raise`
- Built-in exceptions
- Custom exceptions

**External Libraries:** None. Only Python's built-in modules are required.

## Project Structure

```text
student-records-import-validation-tool/
│
├── main.py
├── students_input.json
├── students_valid.json
└── import_errors.txt
```

| File | Purpose |
|---|---|
| `main.py` | Main application logic, file processing, and validation |
| `students_input.json` | Input file containing student records |
| `students_valid.json` | Output file containing accepted records |
| `import_errors.txt` | Log containing rejected records and error messages |

## Input Data Format

The input JSON file contains a list of student records.

Each record includes:

- `student_id`
- `name`
- `department`
- `marks` – A list containing marks for three subjects.

Example:

```json
[
    {
        "student_id": "S101",
        "name": "Aman",
        "department": "CSE",
        "marks": [78, 65, 88]
    },
    {
        "student_id": "S102",
        "name": "Riya",
        "department": "CSE",
        "marks": [35, 72, 61]
    }
]
```

## Validation Rules

A student record is accepted only if:

1. The record is a dictionary.
2. All required fields are present.
3. Student ID, name, and department have the expected data types.
4. Marks contain exactly three numeric values.
5. Every mark is between 0 and 100.
6. Boolean values are not accepted as marks.
7. Student IDs are unique.

Invalid records are rejected with a meaningful error message.

## Exception Handling Concepts Covered

- Identifying syntax, runtime, and logical errors.
- Using `try`, `except`, `else`, and `finally`.
- Handling `FileNotFoundError`.
- Handling `PermissionError` and `OSError`.
- Handling `json.JSONDecodeError`.
- Handling `KeyError`, `TypeError`, and `ValueError`.
- Raising built-in exceptions using `raise`.
- Creating a custom `StudentRecordError` exception.
- Avoiding bare `except` statements.
- Preventing accidental overwriting of existing valid output data.

## How to Run the Project

**1. Clone the repository**

```bash
git clone https://github.com/your-username/student-records-import-validation-tool.git
```

**2. Navigate to the project directory**

```bash
cd student-records-import-validation-tool
```

**3. Run the application**

```bash
python main.py
```

No external package installation is required.

## Example Output

```text
Import started: students_input.json

Accepted: S101 - Aman

Rejected record 2:
marks must contain exactly 3 values between 0 and 100.

Rejected record 3:
missing required field 'name'.

Import completed.

Accepted records: 1
Rejected records: 2

Valid output: students_valid.json
Error log: import_errors.txt
```

*Note: The output is illustrative. Actual results depend on the input JSON file.*

## Important Data Safety Rule

The original input file `students_input.json` must remain unchanged.

If the input file cannot be read or contains malformed JSON, the application must report the error and exit safely. It must not create a misleading empty output or overwrite a previous valid output file.

## Learning Outcomes

Through this project, the following concepts are practised:

- Writing reliable Python programs.
- Handling errors without crashing the application.
- Validating structured JSON data.
- Creating and using custom exceptions.
- Processing valid and invalid records separately.
- Maintaining readable error logs.
- Protecting existing data during file operations.

## Future Improvements

- Add a graphical user interface.
- Support CSV input files.
- Generate detailed student performance reports.
- Add database integration.
- Create an interactive record correction feature.

## Author

**Adeeb Hami**

B.Tech – AI/ML

## License

This project is created for educational and learning purposes.
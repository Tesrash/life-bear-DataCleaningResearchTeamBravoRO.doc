# life-bear-DataCleaningResearchTeamBravoRO.doc

CSV Processing Script
This Python script processes large CSV files to clean data, handle invalid entries, and split or merge CSV files.

Features
Validate Emails: Identifies and exports rows with invalid email addresses.
Detect Duplicates: Finds and exports duplicate rows.
Check for Missing Values: Displays missing values in each column.
Check for Invalid Characters: Detects invalid characters in text fields and exports affected rows.
Rename Columns: Capitalizes the first letter of each column header for consistency.
Split CSV Files: Splits large CSV files into smaller chunks.
Merge CSV Files: Combines CSV chunks into a single file.
Requirements
Python 3.x
Install required libraries with:
bash
Copy code
pip install pandas
How to Use
1. Process a CSV File
Clean your CSV file by validating emails, finding duplicates, checking for missing values, and scanning for invalid characters:

python
Copy code
df = process_csv("your_file.csv", "junk_directory")
Replace "your_file.csv" with the path to your CSV file.
Invalid rows will be saved in the junk_directory.
The cleaning process includes:

Email Validation: Rows with invalid email formats are saved as invalid_emails.csv.
Duplicate Detection: Duplicate rows are exported as duplicate_rows.csv.
Missing Values: Columns with missing values are displayed in the output.
Invalid Characters: Rows with invalid characters in text fields are saved with filenames like invalid_{column}.csv.
Column Renaming: Column headers are updated to start with a capital letter.
2. Split a CSV into Chunks
If your CSV file is too large, you can split it into smaller chunks:

python
Copy code
split_csv_into_chunks("your_file.csv", 500000, "chunk_directory")
Replace 500000 with the number of rows per chunk.
Chunks will be saved in the chunk_directory.
3. Merge CSV Chunks
After processing or splitting CSV files, you can merge the chunks back into a single file:

python
Copy code
merge_csv_chunks("chunk_directory", "merged_file.csv")
The merged file will be saved as merged_file.csv.
Output
The script generates the following files:

invalid_emails.csv: Rows with invalid email addresses.
duplicate_rows.csv: Rows with duplicate entries.
invalid_{column}.csv: Rows with invalid characters in specific columns.
chunk_0.csv, chunk_1.csv: CSV chunks split from the original file.
merged_file.csv: The final merged CSV file combining all chunks.

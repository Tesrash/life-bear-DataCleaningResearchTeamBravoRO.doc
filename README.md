# life-bear-DataCleaningResearchTeamBravoRO.doc

CSV Processing Script
This Python script processes large CSV files to handle invalid email addresses, detect duplicates, find missing values, and check for invalid characters in text fields. It also provides functionality to split large CSV files into smaller chunks and merge them back into a single file.

Table of Contents
Features
Requirements
Installation
Usage
Processing CSV Files
Splitting CSV Files
Merging CSV Chunks
Customization
Output


Features
Email Validation: Identifies invalid email addresses based on a regex pattern and exports them to a CSV.
Duplicate Detection: Detects and exports duplicate rows to a CSV file.
Missing Value Identification: Displays the count of missing values in each column.
Invalid Character Check: Scans columns for invalid characters and exports problematic rows to CSV.
CSV Splitting: Splits large CSV files into smaller chunks.
CSV Merging: Merges previously split CSV chunks into a single file.
Requirements
The script requires the following Python libraries:

pandas - for CSV file manipulation.
re - for regular expression operations.
os - for file and directory management.
You can install the required libraries with:

bash
Copy code
pip install pandas
Installation
Clone or Download the repository:
bash
Copy code
git clone https://github.com/yourusername/csv-processing-script.git
cd csv-processing-script
Install required dependencies:
bash
Copy code
pip install -r requirements.txt
Adjust file paths and parameters in the script to match your specific CSV file locations and needs.
Usage
Processing CSV Files
To process a CSV file, including validating emails, detecting duplicates, identifying missing values, and finding invalid characters, use the process_csv function:

python
Copy code
df = process_csv(file_path, junk_directory)
file_path: Path to your CSV file.
junk_directory: Directory where files with invalid data will be stored.
Example:

python
Copy code
file_path = "/content/mydata.csv"
junk_directory = "/content/junk"

df = process_csv(file_path, junk_directory)
The script will:

Save rows with invalid email addresses to /content/junk/invalid_emails.csv.
Save duplicate rows to /content/junk/duplicate_rows.csv.
Save rows with invalid characters in specific columns (if any) to separate files for each column.
Splitting CSV Files
To split a large CSV file into smaller chunks, use the split_csv_into_chunks function:

python
Copy code
split_csv_into_chunks(file_path, chunk_size, chunk_directory)
file_path: Path to the CSV file you want to split.
chunk_size: Number of rows per chunk.
chunk_directory: Directory where the chunks will be saved.
Example:

python
Copy code
file_path = "/content/mydata.csv"
chunk_size = 500000  # Split into chunks of 500,000 rows each
chunk_directory = "/content/chunks"

split_csv_into_chunks(file_path, chunk_size, chunk_directory)
The script will save each chunk in the specified directory with filenames like chunk_0.csv, chunk_1.csv, etc.

Merging CSV Chunks
To merge multiple CSV chunks into a single file, use the merge_csv_chunks function:

python
Copy code
merge_csv_chunks(chunk_directory, output_file)
chunk_directory: Directory containing the CSV chunks.
output_file: Path to the final merged CSV file.
Example:

python
Copy code
chunk_directory = "/content/chunks"
output_file = "/content/merged.csv"

merge_csv_chunks(chunk_directory, output_file)
The script will combine the chunks into a single file at the specified location.

Customization
Email Column Name
In the process_csv function, the email column is assumed to be named 'login_id'. If your column name is different, adjust this line:

python
Copy code
email_column_name = 'login_id'  # Update this to your actual email column name
Invalid Character Set
By default, the script checks for non-alphanumeric characters and spaces. You can modify the set of allowed characters in the contains_invalid_chars function.

python
Copy code
allowed_chars = "abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789 "
To allow special characters, simply add them to the string.

Output
The following files are generated during processing:

Invalid Emails: invalid_emails.csv (in the junk directory).
Duplicate Rows: duplicate_rows.csv (in the junk directory).
Invalid Character Rows: Files with the pattern invalid_{column_name}.csv (for each column containing invalid characters).
Split Chunks: CSV files named chunk_0.csv, chunk_1.csv, etc., in the specified chunk directory.
Merged CSV: A single merged file from chunks.

# `gpt-batching`: Python tool for the data processing for batch jobs with the OpenAI API.

This repository contains a series of scripts that I developed to classify text data with the OpenAI API. Examples of usage are provided below. 

If you are new to using the OpenAI API I recommend you to start with its documentation, you might also consider the following [information flow diagram](diagram.png) that I elaborated. 

# Usage examples

## `create_jsonl()` 

Divide the data to be sorted into batches in .jsonl format according to the API usage limits. Insert your prompt, maximum token desired and LLM chosen directly in the code.

### Call the function
`create_jsonl`(
    df, 
    batch_size=30000, 
    output_base_name="batch", 
    output_dir="./input_batchs/"
    )

## `upload_jsonl_files()` 

Upload batches to the OpenAI platform

### Call the function

`upload_jsonl_files`(
    "./input_batchs/"
    )

## `create_batch_jobs()` 

Start batch jobs and limit it to the maximum processing available (according to number of calls and weight of each file)

### Call the function

`create_batch_jobs`(
    "uploaded_file_ids.csv", 
    start_file=1, 
    end_file=15
    )

## `update_batch_output_file_id()` 

Update the ID of each batch uploaded to the platform for downloading.

### Call the function

`update_batch_output_file_id`(
    "batch_ids.csv"
    )

## `download_and_process_multiple_files()` 

Download all successfully completed batches

### Call the function

csv_file = "batch_ids.csv" 
download_folder = "./resulting_batches/"  

### Download and process all files in the CSV
`download_and_process_multiple_files`(
    csv_file, 
    download_folder
    )

## `load_jsonl_to_dataframe()` 

Retrieve relevant information from downloaded .jsonl files

### Call the function

output_df = `load_jsonl_to_dataframe`(
    "./resulting_batches/", 
    id_column="post_id", 
    content_column="reasoning"
    )







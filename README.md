# data-transformations-with-python
The purpose of this repo is to build data transformation applications.  The code contains ignored tests.  Please unignore these tests and make them pass.  

## Pre-requisites
Please make sure you have the following installed and can run them
* Python 3.6 or later
* PySpark (`pip install pyspark`)
* PyCharm IDE

The following instructions assumes the command to run Python 3.X is python3

## Setup Process
* Clone the repo
* cd project/src
* Test: `python3 -m unittest`

## Pycharm Setup
* Open downloaded repo in PyCharm
* In Preferences > Project > Project Structure set src directory to Sources (source root)

###


### Wordcount
* Sample data is available in the `src/test/wordcount/data` directory
This applications will count the occurrences of a word within a text file. By default this app will read from the words.txt file and write to the target folder.  Pass in the input source path and output path directory to the spark-submit command below if you wish to use different files.

```
python3 job_runner.py WordCount $(INPUT_LOCATION) $(OUTPUT_LOCATION)
```

Currently this application is a skeleton with ignored tests.  Please unignore the tests and build the wordcount application.

### Citibike multi-step pipeline
* Sample data is available in the `src/test/citibike/data` directory
This application takes bike trip information and calculates the "as the crow flies" distance traveled for each trip.  
The application is run in two steps.
* First the data will be ingested from a sources and transformed to parquet format.
* Then the application will read the parquet files and apply the appropriate transformations.


* To ingest data from external source to datalake:
```
python3 job_runner.py DailyDriver $(INPUT_LOCATION) $(OUTPUT_LOCATION)
```

* To transform Citibike data:
```
python3 job_runner.py CitiBikeTransformer $(INPUT_LOCATION) $(OUTPUT_LOCATION)
```

Currently this application is a skeleton with ignored tests.  Please unignore the tests and build the Citibike transformation application.

#### Tips
- For distance calculation, consider using [**Harvesine formula**](https://en.wikipedia.org/wiki/Haversine_formula) as an option.  
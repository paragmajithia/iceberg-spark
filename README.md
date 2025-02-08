# Summary

This is sample demo to show use of spark and apache ice-berg

# Execution Steps 

Below are 2 options to run the app (with Or without docker)

## Option 1: Execute via docker build 

- Pre-requisite:
    - Docker installed & docker engine running on local machine
    - Machine with min 2 GB RAM
    - Code is checked out into your local machine
- Get 3 containers running (spark-master, spark-worker & spark history server)  using commands below

```
## Start the containers
docker compose up

```

-- Verify if the Spark cluster is running be visiting http://localhost:8080/

- Execute the demo script (from /opt/spark folter)
```
## Bash into spark master container
docker exec -it spark-master bash

## Run demo script
./bin/spark-submit ./scripts/iceberg-demo.py
```  

## Option 2 --> Run without docker

- Pre-requisite
    - pyenv installed (>=3.1.1)
    - Machine with min 2 GB RAM
    - Spark is installed
    - Hadoop (winutils) for windows machine is installed
    - Ensure following env variable is set:
        - SPARK_HOME
        - HADOOP_HOME 

- VS Code Notes
    - Python Lanugage Server: Pylance
    - Pylance settings -> Type checking: basic 

- Create virtual environment with python 3.10.11
```
pyenv versions
pyenv install 3.10.11
pyenv local 3.10.11
pip -V
python -m venv venv
```

- Install pyspark (and other dependencies) in virtual env

```
.\venv\Scripts\activate
pip install -r .\requirements.txt
```

- Add Spark runtime and extension jars in %SPARK_HOME%\jars folder

```
iceberg-spark-runtime-3.4_2.12-1.4.3.jar
iceberg-spark-extensions-3.4_2.12-1.4.3.jar
```  

- Execute the script
```
python .\scripts\iceberg-demo.py
```


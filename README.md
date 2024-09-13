# BigData Solution for Hadoop and Spark.

### Scale your data management by distributing workload and storage on Hadoop and Spark Clusters, explore and transform your data in Jupyter Notebook.

## About The Project

Purpose for this tutorial is to show how to get started with Hadoop, Spark and Jupyter for your BigData solution,
deployed as Docker Containers.

## Pre-requisite

- Apple Silicon might use arm64 branch to install.
- Ensure Docker is installed.

## Start

- Execute `bash master-build.sh` to start  build and start the containers.
- Execute `docker cp mapper.py hadoop-namenode:/mapper.py`
- Execute `docker cp reducer.py hadoop-namenode:/reducer.py`
- Execute `docker cp input.txt hadoop-namenode:/input.txt`
- Execute `docker exec -it hadoop-namenode bash`
- Execute `hdfs dfs -put input.txt /input`
- Execute `hadoop jar /opt/hadoop-3.3.6/share/hadoop/tools/lib/hadoop-streaming-3.3.6.jar\
  -files mapper.py,reducer.py\
  -mapper mapper.py\
  -reducer reducer.py\
  -input /input/input.txt\
  -output /output`
- Execute `hadoop fs -cat /output/part-00000` to see output

## Stop

Execute `bash master-delete.sh` to stop the containers.

### Hadoop

Access Hadoop UI on ' http://localhost:9870 '

### Spark

Access Spark Master UI on ' http://localhost:8080 '

### Jupyter

Access Jupyter UI on ' http://localhost:8888 '


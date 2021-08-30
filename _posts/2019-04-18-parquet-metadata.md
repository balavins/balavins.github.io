Parquet is a quite popular and efficient data-format.
It is structured into row-groups which contain pages of columns.
Each page tends to be futher compressed and encoded with RLE-BP and dictionary encodings.
I would usually like to look at the meta-data of parquet files in detail. 
Download parquet-cli jar from the following page
https://javadoc.io/doc/org.apache.parquet/parquet-cli/latest/index.html 

if you have hadoop installed in your system, you could do the following to look at the meta-data
```
parquet=$1
bin/hadoop jar ~/parquet-tools/parquet-cli-1.12.0-SNAPSHOT-runtime.jar  org.apache.parquet.cli.Main pages file:///$parquet
bin/hadoop jar ~/parquet-tools/parquet-cli-1.12.0-SNAPSHOT-runtime.jar  org.apache.parquet.cli.Main meta file:///$parquet
```

if the parquet file is too big, you could add 
```
export HADOOP_CLIENT_OPTS="-Xmx4096m $HADOOP_CLIENT_OPTS"
```

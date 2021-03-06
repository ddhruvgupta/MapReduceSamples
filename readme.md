### Introduction ###
This repository consists of a series of practice exercises for Map Reduce. 
They are done using python taking advantage of hadoop streaming. 

### Setup ##

Centos OS with Cloudera Hadoop distribution. The VM can be obtained from: http://content.udacity-data.com/courses/ud617/Cloudera-Udacity-Training-VM-4.1.1.c.zip


The following command alias is added to the bashrc file: 
- open bashrc: `gedit ~/.bashrc`

- create alias:
	```bash
	run_mapreduce() { hadoop jar /usr/lib/hadoop-0.20-mapreduce/contrib/streaming/hadoop-streaming-2.0.0-mr1-cdh4.1.1.jar -mapper $1 -reducer $2 -file $1 -file $2 -input $3 -output $4}
	alias hs=run_mapreduce`
	```
	
## Testing ##
- create test data 
`tail -100  ./data/purchases.txt > test`
 
- test mapper individiually
`tail -1000 ../data/purchases.txt > testdata`
`./mapper.py < testdata > inp_red`
`tail inp_red`

### Run Map Reduce Job: ###
`hadoop fs -put ../data/purchases.txt input`
`hadoop fs -ls /data`
`hs mapper.py reducer.py /data/input /data/out1`

### View Output ###
`hadoop fs -tail /data/out1/part-00000`


____________________________________________________________________________________________________

- Assignment 1: mapper-reducer for finding total sales per item category
- Assignment 2: Find the monetary value for the highest individual sale for each separate store

- Assignment 3: Total Number of sales and sum of sales for each store
	Ans: 4138476	1034457953.26

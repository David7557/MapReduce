# MapReduce
MapReduce projects can be used to process a wide variety of data sets, including text files, images, and sensor data. They are a powerful tool for processing large data sets in a parallel and distributed manner.

#How MapReduce Works

input format and record reader-----passing the contents to mapper..

input file:

hadoop is fun
fun with hadoop

split1: 0 ,hadoop is fun
split2: 1 ,fun with hadoop


Input to mapper:Key: offset value(0)long
                value: entire line(hadoop is fun)text 
map()1: hadoop,1
	is,1
	fun,1

map()2: fun,1
	with,1
	hadoop,1

output of mapper:key,value
                map1:   (hadoop,1),(is,1),(fun,1)
		map2: (fun,1),(with,1),(hadoop,1) 

                  
Shuffling: hadoop-{1,1}
is-{1,}
fun-{1,1}
with-{1}

input to reducer:key,list of values
                  hadoop--{1,1}, is--{1}, fun--{1,1},with--{1}

output of reducer:  key,value
                    hadoop, 2
                      is,1
                      fun,2
                     with,1



#Steps to run map reduce:

1. Open cloudera quickstart vm
2. open eclipse
3. Go to file--new project--create java project
4. Right click on your java project on LHS--create a new class such as wordcount.
5. Now write the program in your class.
6. Configure your program to hadoop jar files(*hadoop-common-2.2.0.jar and *hadoop-mapreduce-client-core-2.2.0.jar)
6.1  Right click on your class name on LHS --build configure path--add hadoop jar files to your Program
7. Build the jar file of your program.
Right click on your class name on LHS--export-click jar file inside java--select the 
export destination of jar file--select the folder in which to save program- select the main class--finally finish

8. Go to terminal: hadoop jar <location of jarname of your program> /input file path /output directory path
                   hadoop jar /home/cloudera/Desktop/wc.jar /a.txt /wcoutput


9. See output:
    hadoop fs -ls /output directory
    hadoop fs -cat /wcoutput/part-r-00000
    
input
hadoop fs -put /home/cloudera/desktop/adad.txt hdfs:/


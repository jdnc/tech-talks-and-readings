* Video: [https://www.safaribooksonline.com/library/view/introduction-to-the/9781771376150/]
* Title: Introduction to the Hadoop Technology Stack

# Notes 

* hadoop is a storage solution for storing very large files
* hdfs is the actual filesystem that manages storage on a hadoop cluster
* hadoop cluster is made up of nodes. These nodes have both compute and storage capacity
* Typically there are several worker nodes and 1-2 master nodes
* Master node is responsible for tracking where each file is
* Clients will directly get the data from the right worker node, after finding the location from the master node
* Adding more worker nodes will linearly scale up both the compute and the storage capacity of the cluster
* In hdfs, each file is divided into blobs of 64-128MB. These blobs are then parallely stored on different storage nodes across the cluster
* The blobs are also replicated, to increase fault tolerance. Typicaly 3x replication is the norm. Files that are very much in demand can be replicated more, so that the client can access these files in parallel.

* Yarn is the resource / application manager that runs various processing tasks on the hadoop cluster.
* It supports several processing frameworks like map-reduce / spark / etc
* Pig and hive are sql like languages that Yarn recognizes and will compile into the appropriate map-reduce tasks in java

* Apache flume, apache kafka, Apache storm,  etc are ingestion frameworks that will allow loading data into hdfs from external sources.
* Mahout is a machine learning framework that is optimized to run on the top of hadoop

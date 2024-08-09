This programming assignment covers sort through Hadoop and Spark on multiple nodes. You must use a
Chameleon node using Bare Metal Provisioning (https://www.chameleoncloud.org). You must deploy Ubuntu
Linux 16.04 using either “compute-skylake” or “compute-haswell” nodes, at either UC or TACC sites. Once
you create a lease (up to 7 days are allowed), and start your 1 physical node, and Linux boots, you will find
yourself with a physical node with 24 CPU cores, 48 hardware threads, 128GB to 192GB of memory (depending
on if its Haswell or Skylake), and 250GB SSD hard drive. You will install your favorite virtualization or
containerization tools (e.g. virtualbox, KVM, qemu, Docker, lxc/lxd), and use it to deploy two different
VMs/containers with the following sizes: small.instance (4-cores, 8gb ram, 50gb disk), and large.instance (16-
cores, 32GB ram, 200gb disk).

This assignment will be broken down into several parts, as outlined below:
Hadoop File System and Hadoop Install: Download, install, configure, and start the HDFS system (that is part
of Hadoop, https://hadoop.apache.org) on a virtual cluster with 1 large.instance, and then again on a virtual cluster
with 4 small.instances. You must turn off replication, or you won’t have enough storage capacity to conduct your
experiments.

Datasets: Once HDFS is operational, you must generate your dataset with gensort
(http://www.ordinal.com/gensort.html); you will create 4 workloads: data-1GB, data-4GB, data-16GB, and data64GB. You may not have enough room to store them all, and run your compute workloads. Make sure to cleanup
after each run. Remember that you will typically need 3X the storage, as you have the original input data,
temporary data, and output data. Configure Hadoop to run on the virtual cluster, on 1 large.instance and 4
small.instances. You may need a 5th virtual machine to run parts of Hadoop (e.g. name node, scheduler, etc).
#
Spark Install: Download, install, configure, and start Spark (https://spark.apache.org). Note that you will need
the HDFS installation for Hadoop to work from and to.
Shared Memory Sort: Run your shared memory sort from HW5 on the small.instance and large.instance defined
above on the different datasets.
#
Linux Sort: Run the Linux Sort on the small.instance and large.instance defined above on the different datasets.
Hadoop Sort: Implement the HadoopSort application (you must use Java). You must specify the number of
reducers to ensure you use all the resources of the 4-node cluster. You must read the data from HDFS, sort it,
and then store the sorted data in HDFS and validate it with valsort. Measure the time from reading from HDFS,
sorting, and writing to HDFS; do not include the time to run valsort.
Spark Sort: Implement the SparkSort application (you must use Java). Make sure to use RDD to speed up the
sort through in-memory computing. You must read the data from HDFS, make use of RDD, sort, and write the
sorted data back to HDFS, and finally validate the sorted data with valsort. Measure the time from reading from
HDFS, sorting, and writing to HDFS; do not include the time to run valsort.
Performance: Compare the performance of your shared-memory external sort, the Linux “sort” (more
information at http://man7.org/linux/man-pages/man1/sort.1.html), Hadoop Sort, and Spark Sort on a 4-node
cluster with the 1GB, 4GB, 16GB, and 64GB datasets. Fill in the table below, and then derive new tables or figures
(if needed) to explain the results. Your time should be reported in milliseconds.

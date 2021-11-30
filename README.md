# TBD

## Description

An optimized version of parallel PageRank has been implemented using OpenMP and the implementation is in the folder `pagerank-openmp` Additionally, a simple unoptimed parallel version of PageRank has been implemented using Pthreads. This has been done to compare the efforts required to modify a sequential program using OpenMP and Pthreads.

## Note
Please use `crunchy1` machine and `GCC 4.8.5` for compilation and test.

## Execution Instructions

### OpenMP

The `data` folder contains the datasets used in this project. Since, they are huge, we are submitting a compressed version of these. In order to extract a dataset, please run the following command:
```
$ cd openmp/data/
$ gzip -d <dataFile name>
```
For example, if you want to use the dataset 'web_Google', run the following command:
```
$ cd openmp/data/
$ gzip -d simple_web-Google.graph.gz
```
This will create a text file called `simple_web-Google.graph`.

<br/>

`tools` folder contains script to convert text graphs to binary graphs which is in turn used by the PageRank program. In the `data` folder, all the graphs starting with `simple_` are the text graphs. Inorder to convert a `simple` graph to binary graph, run the command:
```
$ cd openmp/tools/
$ make
$ ./graphTools text2bin <simple input graph filename> <binary output graph filename>
```
For example, to convert the above `simple_web-Google.graph` to binary, run the command:
```
$ cd openmp/tools/
$ make
$ ./graphTools text2bin ../data/simple_web-Google.graph ../data/binary_web-Google.graph
```
This will create a binary file `binary_web-Google.graph` in the data folder

<br/>

Now, to compile and run the PageRank program, go to the directory containing Makefile and execute the make command. This will create an executable called `pr`:
```
$ cd openmp/pagerank/
$ make
```
Next, run the following command to launch the program on a particular graph using a certain number of threads:
```
$ ./pr <path to graph> <number of threads> 
```
For example, run the following command to launch the program on the web-Google graph using 16 threads:
```
$ ./pr ../data/binary_web-Google.graph 16 
```

<br/>

Scheduling policy and chunk size can be changed by modifying the `page_rank.cpp` file.

### Pthreads

The `data` folder contains the datasets used in this project. Since, they are huge, we are submitting a compressed version of these. In order to extract a dataset, please run the following command:
```
$ cd openmp/data/
$ gzip -d <dataFile name>
```
For example, if you want to use the dataset 'web-Google.txt.gz', run the following command:
```
$ cd openmp/data/
$ gzip -d web-Google.txt.gz
```
This will create a text file called `web-Google.txt`.

<br/>

Now, to compile and run the PageRank parallel program, go to the directory `pagerank_parallel` and execute the make command. This will create an executable called `pagerank_pthreads`:
```
$ cd pthreads/pagerank_parallel/
$ make
```
Next, run the following command to launch the program on a particular graph using a certain number of threads:
```
$ ./pagerank_pthreads <path to data file> <number of vertices in the graph> <convergance threshold of pageRank> <d used by PageRank algorithm - describeb in report> <number of threads>
```
For example, run the following command to launch the program on the web-Google graph using 16 threads:
```
$ ./pagerank_pthreads ../data/web-Google.txt 1000000 0.0000001 0.3 16
```

<br/>

To compile and run the PageRank serial program, go to the directory `pagerank_serial` and execute the make command. This will create an executable called `pagerank_serial`:
```
$ cd pthreads/pagerank_serial/
$ make
```
Next, run the following command to launch the program on a particular graph:
```
$ ./pagerank_serial <path to data file> <number of vertices in the graph> <convergance threshold of pageRank> <d used by PageRank algorithm - describeb in report>
```
For example, run the following command to launch the program on the web-Google graph:
```
$ ./pagerank_serial ../data/web-Google.txt 1000000 0.0000001 0.3
```

<br/>

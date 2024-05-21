


# ReadMe: A Clique Partitioning-Based Algorithm for Graph Compression

## The provided Git repository includes the following:

- Implementation of both Feder-Motwani (FM) and CPGC algorithm in C `fm.c` and `cpgc.c`, respectively.
- Implementation of Dinitz's algorithm for both original bipartite and the compressed graph in C `dinics_bi.c` and `dinics_tri.c`, respectively.
- Batch scripts to test FM for multiple experiments: `fmbatchScript.sh`
- Combined batch scripts to test CPGC and Dinitz's algorithm for multiple experiments: `cpgcbatchScript.sh`
- Folder with name `datasets` which includes the Python code to generate bipartite graphs in .mtx format with the corresponding code `simpleGraphGenerator.py`, a batch script to test the Python code for bipartite graphs for multiple experiments: `simpleGraphGenerator.sh`, and a sample bipartite graph in .mtx format: `bipartite_graph_32_80_1.mtx`.

**Note**: To test the above algorithms’ code, run them in the following order:

1. Run the `simpleGraphGenerator.py` code via its batch script `simpleGraphGenerator.sh` to generate bipartite graphs and use them as inputs for FM (`fm.c`), CPGC (`cpgc.c`), and Dinitz's algorithm (`dinics_bi.c`) code.
2. Compile and run FM, CPGC and Dinitz’s algorithms for both bipartite and tripartite graphs.


## The implementation of the algorithms in the paper have been organized as follows:

### Folder: datasets

**Programming Language**: Python  
**Version**: 3 and above

1. We generated the original bipartite graphs in Python for instances with |U| = |W| = n number of nodes equal to $2^i$, where i = 5, 6, ..., 15 and having five different densities: p = 0.80, 0.85, 0.90, 0.95, and 0.98.

2. The corresponding code `simpleGraphGenerator.py` in folder `datasets` generates such bipartite graphs.

3. To generate a input bipartite graph do the following steps:  
-  change the current directoy to `datasets` and
-  run the `simpleGraphGenerator.py` python file, it takes three arguments in the following sequence:
   - nodes, i.e., the number of vertices in the left partition of given graph (eg. 32768),  
   - density, i.e., the density of the given graph (eg. 98), and  
   - experimentNo, i.e., the experiment number (eg. 1).  
-  run the following command ```python3 simpleGraphGenerator.py 32768 98 1```,
-  it will generate `bipartite_graph_nodes_density_experimentNo.mtx` bipartite graph in the current `dataset` directory. 

4. T0 generate multiple input bipartite graphs do the following steps:
- updatet number of vertices, dnesity and experiment number in the `simpleGraphGenerator.sh` bash file as required
- change the current directoy to `datasets` and
- run the following command ```bash simpleGraphGenerator.sh```
- this will generate the requested input bipartite graphs in the current `dataset` directory.


**Programming Language**: C  
**Compiler**: gnu  
**Version**: tested with version 7 and 9

1. We implemented Feder-Motwani (FM) algorithm (`fm.c`), CPGC algorithm (`cpgc.c`), and Dinitz’s algorithm for both original bipartite (`dinics_bi.c`) and compressed graph (`dinics_tri.c`).

2. To compile the FM and CPGC code use the following commands, respectively:
- change the directory to the main directory (i.e. the main folder of the repo) in the terminal,
- for compiling FM code use ```gcc fm.c -lm -o fm```
- for compiling CPGC code use ```gcc cpgc.c -lm cpgc```

3. To run the FM and CPGC code use the following commands, respectively:
- change the directory to the main directory (i.e. the main folder of the repo) in the terminal,
- for executing FM code use ```./fm nodes density experiment delta```
- for executing CPGC code use ```./cpgc nodes density experimentNo delta```
- where, 
   a) nodes, i.e., the number of vertices in the left partition of given graph,  
   b) density, i.e., the density of the given graph,  
   c) experimentNo, i.e., the experiment number,  
   d) delta, i.e., the constant δ ($0 < \delta \leq 1).  

4. To run the FM executable files for multiple experiments through a batch script use the following commands:

8. To run the CPGC and Dinitz algorithms executable files for multiple experiments through a batch script use the following commands:

9. The output for FM and CPGC will be stored as csv files with names: `fm_results.csv` and `cpgc_results.csv`, respectively. Both outputs includes six arguments in the following sequence:  
a) nodes, i.e., the number of vertices in the left partition of given graph,  
b) density, i.e., the density of the given graph,  
c) experimentNo, i.e., the experiment number,  
d) delta, i.e., the constant δ,  
e) compression_ratio, i.e., compression ratio of FM or CPGC algorithm, and  
f) execution_time, i.e., the execution time of FM or CPGC algorithm.  

10. The output for Dinitz’s algorithms will be stored as `bipartite_dinics_results.csv` and `tripartite_dinics_results.csv` while prints eight arguments in the following sequence:  
a) nodes, i.e., the number of vertices in the left partition of given graph  
b) total_nodes, i.e., the total vertices in the graph, which includes the vertices in source, left partition, middle partition, right partition, and sink,  
c) density, i.e., the density of the given graph,  
d) experimentNo, i.e., the experiment number,  
e) delta, i.e., the constant δ,  
f) maximumFlow, i.e., maximum matching in a given graph,  
g) run_time, i.e., execution time for the Dinitz's algorithm,  
h) total_run_time, i.e., total execution time including reading the .mtx files.  








#  Maze  solver

### About maze solver project :--
In this project we build a python program that runs as a command-line tool.It should take the input and output file name as command-line arguments.Using the square matrix present in the input file it should generate a path to reach the end of the maze and put it in the output file.If the maze is unsolvable, it should return -1 as the only value in the output file.In the maze matrix, 0 means the block is a dead end and 1 means the block can be used in the path from source to destination.


# Following are the import we use in this project:--
``` 
1. Defaultdict
2. Sys
3. Argparse
```

# Run command:-- 
```
                   maze.py -i inputfile.txt -o outputfile.txt -s 0,0 -d 4,4 
```

when we don't give through inputfile and outfile in command it will take default value.
s = source point 
d = dest point

### inputfile:-
first we give size of matrix
and then we give path like:--
```
5
1 1 0 0 0
1 1 1 1 0                                        
0 1 1 1 0                                         
1 1 1 1 0
1 1 1 1 1

```
It take only n*n matrix when our matrix is solve it show result in outputfile like-
```
1 1 0 0 0
0 1 0 0 0
0 1 0 0 0
0 1 0 0 0
0 1 1 1 1
```
maze is solved
#### If the maze is unsolvable, it should return -1 in outputfile. 

# Description about the code:--

- we use the graph class in this class in this we use defaultdict(list) for adding edge to graph and we use edge and vertices of graph.
```
class Graph:
    def __init__(self):
        self.graph = defaultdict(list)
```
- then we add edge in this graph with using add_edge we take two parameter u and v and append them.
```
def add_edge(self, u, v,weight=1):
        self.graph[u].append(v)
        self.graph[v].append(u)
```
- then we use connect function for saw u and v connect with graph or not when they connect with graph it return true other then it return false.
```
if u in connected_vertex and v in connected_vertex : 
       return True
return False
```
- we use dijkstra algorithm for find the shortest path form one particular starting node to all other nodes in the graph.In this we use distance instance variable in the vertex class.
The value that we use to determine the order of the objects in the priority queue is distance.when a vertex is first created distance is 
Very large.
```
dist = {}
        vertex_visited = {}
 
        for i in self.graph:
            if i == node:
                dist[(node,i)] = 0
            else:
dist[(node,i)] = 10 ** 9

```
- we use strc_to_dest in this function we go source point to dest point. In this function we find the path if we able to find the path we return src_to_dest and if we are not able to solve this we return -1.
```
src_to_dest = set(src_to_dest)
            return src_to_dest
            return -1
```
- we use main function in this function we use argparse for adding the argument in this function we add [ -i ] argument for input file and [ -o ] argument for output file and for source we add     [ -s ] or we add argument for dest [ -d ].
```
parser = argparse.ArgumentParser()
    parser.add_argument('-i' ,type=str , default='inputfile.txt',
    help='which file for input')
    parser.add_argument('-o',type=str , default='outputfile.txt',
    help='which file for output')
```
- then we read inputfile and give source or dest point and check our given input matrix is n*n or not when matrix is n*n is give output  in outputfile.
```
input_file = open(args.i , "r")
    order = input_file.readline()
    input_file.close()
    
 output_file.write(str(temp_list))
        output_file.close()    
    
```


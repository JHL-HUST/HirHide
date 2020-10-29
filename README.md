# HirHide
Edited by [Chao Li](https://github.com/lichaoaaron).

## Compiling
Before compiling, the following software should be installed in your system.

+ g++
+ Xeltex
+ R packages



Compile both the base algorithms and the HirHide program.

​	```$ sh compile.sh```

After compiling, you should see a binary file

​	```$ ./Main```

## How to Run
Rename the graph file to "graph", and put it into director

​	```$ ./data/GRAPH_NAME/```

+ The graph file's first line indicating the number of vertex.
+ The following lines containing 'i j w' representing an edge between (i,j) with weight w.
+ Then write a config file for the graph , named "GRAPH_NAME.config" . See configuration details in the next section.

Run HirHide using command:

​	```$ ./Main GRAPH_NAME.config```
### Example
Run 2-layers synthetic data:

​	```$ ./Main config/synl2.config```

You will find the community detection results in:

​	```$ ./result_directory/{maxLayer, maxOriginal}*.gen```

You can find the ground truth communities in:

​	```$ ./data/synl2/Layer1.gen```
​	```$ ./data/synl2/Layer2.gen```
#### TIPS

The weakening method 'ReduceWeight' in paper indicates the 'Frameworks' should be 'Reduce++' and the 'WeightedGraph' should be TRUE.

## Code Structure
### Framework
The current framework is implemented in some headfiles like 'Framework_Reduce.h' and the base class is 'Framework.h'.

The most important function that need to be implemented is 'calcNextLayerGraph(Graph cur,Community comm)', which gives the current graph and a set of community, return value is the reduced graph.

### Base Algorithms
The current framework is implemented in some headfiles like 'SingleLayer_Modularity.h' and the base class is 'SingleLayer_Method.h'.

The most important function that need to be implemented is 'generateCommunity(string graphFile,string communityFile)', which takes in the graph file and using the algorithm to generate the communities and save in communityFile.

## Announcements
### Licence
Based on the article "Hierarchical hidden community detection for protein complex prediction" Li, C., He, K., Liu, G., & Hopcroft, J. E. (2019).[[arXiv](https://arxiv.org/abs/1910.03337)]

This program is free software: you can redistribute it and/or modify it under the terms of the GNU General Public License as published by the Free Software Foundation, either version 3 of the License, or (at your option) any later version.

This program is distributed in the hope that it will be useful, but WITHOUT ANY WARRANTY; without even the implied warranty of MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU General Public License for more details.

You should have received a copy of the GNU General Public License along with this program. If not, see http://www.gnu.org/licenses/.

### Notification
Please email to us or setup an issue if you have any problems or find any bugs.

Please cite our papers if you use the code in your paper:

        @article{li2019hierarchical,
      title={Hierarchical hidden community detection for protein complex prediction},
      author={Li, Chao and He, Kun and Liu, Guangshuai and Hopcroft, John E},
      journal={arXiv preprint arXiv:1910.03337},
      year={2019}
    }
        
        @article{heli2018hidden,
        title = "Hidden community detection in social networks",
        journal = "Information Sciences",
        volume = "425",
        number = "Supplement C",
        pages = "92 - 106",
        year = "2018",
        issn = "0020-0255",
        doi = "https://doi.org/10.1016/j.ins.2017.10.019",
        url = "http://www.sciencedirect.com/science/article/pii/S0020025517310101",
        author = "Kun He and Yingru Li and Sucheta Soundarajan and John E. Hopcroft",
        keywords = "Community detection, Hidden community, Structure mining, Social networks"
        }
## Acknowledgement
In the program, we incorporates some open source codes as baseline algorithms from the following websites:

+ [Link Communities](https://github.com/bagrow/linkcomm)

+ [OSLOM](http://www.oslom.org/software.htm)

+ [Louvain Method for Modularity](https://sourceforge.net/p/louvain/code/ci/default/tree/)

+ [Infomap](http://www.mapequation.org/code.html)
+ [ClusterONE](https://github.com/ntamas/cl1)
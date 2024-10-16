a serach problem consists of: 

- a state space . set of all possible state where youc an be . 

- a start state . the state from where the search begins 

-  a goal state . a fuction that  looks at the current state returns whether or not it is the goal state . 

- the solution to a serch problme is a sequence of actions called the plan that tranforms the start statte to the goal state . 

- this plan is acheived throught serach algorithms 




## TYPES OF SEARCH ALGORITHMS 

there are far too many powerful seach algorithms out there to fit in a single article instead , this article will discuss six of the fudamental search algorithms , divide into tow categories as shown below 

![image](https://media.geeksforgeeks.org/wp-content/uploads/AI-algos-1-e1547043543151.png)

### UNINFORMED SEARCH ALGORITHMS 

the search algorithms in this section have no additional information on the goal node . 
other than the one proivided in the problem definaiton . the palin to reach the gaol state from the start state differ only by te order and /or lenght of actions . unifnformed search is also called blind search . these algorithms can only generate the successors and differentaaete between the goal state and non goal sate . 

1. depth first search 
1. breadth first search 
1. uniform const search 


each of these algorihtms will have : 


- a problme graph , constaingin the start node S and goal node G . 

- a strategy , describing the manner in which the graph will be travesrsed to get to G . 

- a fringe , which is a data stracute used to store all the possible states ( nodes) that you can go from the curent states . 

- a treee that results while traversing the goal node . 

- a solution plan , which the sequence of node from S to G. 


### DEPTH FIRST SEARCH : 


depth first search is an algorithm form tranversing or searching tree or graph data structres . the algorithm start at the root node ( selecting aribitrary node as the root node in the caseof a graph ) and explres as far as possible algont each branc before backtrackgin it uses last in first out starategy and hence it is imprementaioted usng a stack . 


d  = the depth of the search tree = the number of levels of the search tree. 
n^i  = number of nodes in level i        . 

Time complexity: Equivalent to the number of nodes traversed in DFS. T(n) = 1 + n^2 + n^3 + ... + n^d = O(n^d)        
Space complexity: Equivalent to how large can the fringe get. S(n) = O(n \times d)        
Completeness: DFS is complete if the search tree is finite, meaning for a given finite search tree, DFS will come up with a solution if it exists. 
Optimality: DFS is not optimal, meaning the number of steps in reaching the solution, or the cost spent in reaching it is high.


### BREADTH FIRST SEARCH : 


breadth first search is an algorithm for tranversing or seach tree or graph data structes . it starts at the tree root ( or some arirary node of a graph , sometimes referred to as a search key ), and explores all of the neighbor node at the present depth priour to moving on to the nodes at the next dep level . it is implmented using a queue 


 s        = the depth of the shallowest solution. 
n^i        = number of nodes in level i        . 
Time complexity: Equivalent to the number of nodes traversed in BFS until the shallowest solution. T(n) = 1 + n^2 + n^3 + ... + n^s = O(n^s)        
Space complexity: Equivalent to how large can the fringe get. S(n) = O(n^s)        
Completeness: BFS is complete, meaning for a given search tree, BFS will come up with a solution if it exists. 

Optimality: BFS is optimal as long as the costs of all edges are equal. 


### UNIFORM COST SEARCH 


ucs is different from BFS and DFS becuase hee the cost come into play . in other worlds , travesrsing via different edges might not have the same cost . the goal is to find a path where the cumulative sum is the least . 


cost of a node is defined as 

cost(node) = cumulative cost of all nodes from root 

cost(root) = 0 

example 

quiz : which solution would ucs find to move fom node S to node G if run on the graph below ? 


![image](https://media.geeksforgeeks.org/wp-content/uploads/question-with-weights-e1547119768425.png)


soluton : the equivalent search tree for the above graph is as follows . hte cost of each ndoe is the cumultiave cost of reachin gthat node form the root . based on the ucs strategy , the path with the lest cumulative cost is chosen . note that due to the many options in the fringe , the algorithm expleres most of them so long as there cost is low , and discards them when a lower cost path is fould ; these diescareed travesrsal are not shown belwo the actual traversal is shown in blue . 


![imFW](https://media.geeksforgeeks.org/wp-content/uploads/UCS-e1547120855219.png)

PATH S->A->B->G
COST : 5


ADVANTAGES 

- ucs is complete only if states are finite and there should be no loop with zero weight . 

- ucs is optimal only if there is no negative cost . 





DISADVANTAGEES 


- explores options in every direction 

- no information on gaol location 



## INFORMED SEARCH ALORITHMS 


here , the algorithms have inforamtion on the gaol stae , which heps in more afficient search . this information is obtained by something called a heuristic , in htis section 
we will discuss the following search algorithms . 




1. greedy search 

1. A * tree search 

1. A * graph search 


search heuritics : in an informed search , a heuristic is a fuction that estimates how close a stae is to the goal staet . for example 

- manhatan distance , euclidean distance etc. different heuristics are used in different informed algorithm discussed below 



## GREEDY SEARCH 


in greedy search , we expand the node closest to the gal node . the closesness is estimated by a heauristic h(x)



heuristic : a heuristic h is definead as h(x)  = estimate of distance of node x formt he gaol node . 

lower the value of h(x) closer is the node form the goal .




strategh : expand the node colsest tothe gaol stae   , ie expand the ndoe with a lower h value . 


EXAMPLE 


quiz: find path form s to g using greddy searhc . the heuristic vale h of each node below the name of hte node . 



![image](https://media.geeksforgeeks.org/wp-content/uploads/greedy-ques-e1547130916483.png)


solution : starting from s , we can traverse to a(h=9) or d(h=5) . we choose d . as it has the lower heuristic cost . 

now fromd , we can move to b(h=4) or e(h=3) . we choose e with a lower heuristic cost . finally . from e we go th g(h=3) we choose e and finaly from e we o th e g . this entire travesal is shown below 



![image](https://media.geeksforgeeks.org/wp-content/uploads/greedy-ans-e1547132293499.png)

ADVANTAGES : 

work well with informed search problmes with fewr steps to each a goal . 


DISADVANTAGES 

can turn into uguided DFS in he worst case . 


## A * TREE SEARCH 

a * tree searhc or simply knwon as a * searhc , combines the strengths of uniform costsearch and greddy searh . in this search , the heuristic is the summation of hte cost in ucs , dnoted by g(x) . and the cost in the greddy searhc , denaoted by h(x) the summed cost is denoted by f(x) 


example 


QUIZ: 

find the path to reach from s to g using a* search 

![image](https://media.geeksforgeeks.org/wp-content/uploads/a-star-ques-e1547134645748.png)


Solution. Starting from S, the algorithm computes g(x) + h(x) for all nodes in the fringe at each step, choosing the node with the lowest sum. The entire work is shown in the table below. 

Note that in the fourth set of iterations, we get two paths with equal summed cost f(x), so we expand them both in the next set. The path with a lower cost on further expansion is the chosen path. 


## A* GRAPH SEARCH 

- atree seach works well , expect that it takes time rexploring the racnes it has alerady explored . in other worlds if ithe ame node has expanded twice in i different bracnes of the search tree . a search might explore both of those brances thus wasting time . 


- a graph search or simply graph search , removes theis limitaion by addiing this rule : do not expadn the same node more than once . 


- heuristic . graph search is optmal only when the forward cost between two successive node a and b given by h(a) -h(b) , is less than or equeal to the backward cost between those two nodes g(a ->b) tis property of the graph search heuristic is called cosistency . 


example 


QUIZ: use searches to find pat from s to g in the follwing graph  . 

![image](https://media.geeksforgeeks.org/wp-content/uploads/a-star-ques-e1547134645748.png)

teh soltion . we solve this question pretty much the same way we solved last queion . but in this case , we keep a track of nodes explred so tha we dont re expler them . 
![image](https://media.geeksforgeeks.org/wp-content/uploads/graph-ans-e1547141422493.png)

PATH : S-D-B-E-G

COST : 7 




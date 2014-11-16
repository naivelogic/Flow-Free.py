Flow-Free
==========

How to play Flow Free  

The objective in the game Flow Free,  is to connect each dot of the same color in a continuous line. The path of the line can not cross or overlap to a color dot/path that is not the same color. Finally before the level is complete, you cant leave a single piece of the grid uncovered.  Once you start working your way though the game, each level will gradually become unlocked. I found it extremely useful to work each level in order. As the levels increase, each level pack will becoming bigger. This will increase the grid size and also add additional dots. 

FlowFreeSolution.py

Objective: Find out the most efficient way of finding the shortest path between 2 nodes in a graph with a connecting edge cost that goes through the subset of nodes. 

Solution: Return a list with the tiles coordinates searched when looking for goal node. 

>>>> Here is a video that will assist in implementing in Python. Check it out here: http://youtu.be/JXyli5UzH10
<iframe width="420" height="315" src="//www.youtube.com/embed/JXyli5UzH10" frameborder="0" allowfullscreen></iframe>


Color Connect Algorithm [CCA]: A Recursive Walk



My strategy was use a nested list of integers to represent the map locations maze as an adjacent matrix. 
Identify and map each dot and their corresponding dot.
Path1 list = starting point
Path2 list = ending point
Use a nested list of numbers to visualize as the Flow Free map. 
The values used in the maze are the following:
0: empty cells
-1: Noncurrent starting or ending points
1: Starting Point
'x': Ending Point

Start from the current starting point that is set to '1' and move recursively to all of its 0 neighbors and set to '2'. Append to all 2's to the list. Then mark all of the '0' neighbors of '2' to '3' and append to the list. This will recursively happen until the destination of cell 'x' is reached.

When cell 'x' has been reached, we know have found the path from our starting dot to the ending dot. To find our way back we will again recursively move from 'x'-1 until we have reached 1=1. There should only be one cell that is marked with a '1'. 


Save path and move to the next starting and ending point in the list still path1|2 is empty. 


For an indepth explination view my blog here: http://plhale.blogspot.com/2014/11/flow-free-color-connect-solution-5x5.html 

### Portals

https://www.metacareers.com/profile/coding_puzzles?puzzle=544961100246576

You've found yourself in a grid of cells with 
�
R rows and 
�
C columns. The cell in the 
�
ith row from the top and 
�
jth column from the left contains one of the following (indicated by the character 
�
�
,
�
G 
i,j
​
 ):
If 
�
�
,
�
G 
i,j
​
  = ".", the cell is empty.
If 
�
�
,
�
G 
i,j
​
  = "S", the cell contains your starting position. There is exactly one such cell.
If 
�
�
,
�
G 
i,j
​
  = "E", the cell contains an exit. There is at least one such cell.
If 
�
�
,
�
G 
i,j
​
  = "#", the cell contains a wall.
Otherwise, if 
�
�
,
�
G 
i,j
​
  is a lowercase letter (between "a" and "z", inclusive), the cell contains a portal marked with that letter.
Your objective is to reach any exit from your starting position as quickly as possible. Each second, you may take either of the following actions:
Walk to a cell adjacent to your current one (directly above, below, to the left, or to the right), as long as you remain within the grid and that cell does not contain a wall.
If your current cell contains a portal, teleport to any other cell in the grid containing a portal marked with the same letter as your current cell's portal.
Determine the minimum number of seconds required to reach any exit, if it's possible to do so at all. If it's not possible, return 
−
1
−1 instead.


```js

function getSecondsRequired(R, C, G) {
  // Write your code here
  // once walked, should mark to wall
  // BFS => shortest path

  //time complex: O(RC)
  //space complex:o(RC)
  
  
  var graph = new Array(26).fill().map(()=>new Array())
  var charCodeA = "a".charCodeAt(0)
  var start
  // build the linkGraph
  for(var i = 0;i<R;i++){
    for(var j = 0;j<C;j++){
      var curCell = G[i][j]
      if(curCell=="S"){
        G[i][j]="#"
        start = [i,j]
      }

      var ind = curCell.charCodeAt(0)-charCodeA
      if(0<=ind&&26>ind) graph[ind].push([i,j])
    }
  }
  // design the bfs principal
  var moveOptions = (x,y) =>{
    var options = []
    var ind = G[x][y].charCodeAt(0)-charCodeA
    console.log(G[x][y], ind,graph[ind])
// If your current cell contains a portal, teleport to any other cell in the grid containing a portal marked with the same letter as your current cell's portal.
    if(graph[ind]&&graph[ind].length){
      console.log(graph[ind])
      for(var [a,b] of graph[ind]){
        options.push([a,b])
      }
      console.log(G[x][y],options)
      graph[ind]=[]
    }
      // Walk to a cell adjacent to your current one (directly above, below, to the left, or to the right), as long as you remain within the grid and that cell does not contain a wall.
    if(x+1<R)options.push([x+1,y]) 
    if(x-1>=0)options.push([x-1,y])
    if(y+1<C) options.push([x,y+1])
    if(y-1>=0)options.push([x,y-1])
      
    return options
  }
  var cnt = 0;
  var queue = [start]
  // implement bfs
  while(queue.length){
    var len = queue.length
    cnt ++
    for(var i =0;i<len;i++){
      var node = queue.shift()
      var [x,y] = node
      var options = moveOptions(x,y)
      console.log([x,y],options,cnt)
      for(var [a,b] of options){
        if(G[a][b]=="E"){
          console.log([x,y],[a,b],"ans")
          return cnt
        }else{
          if(G[a][b]!=="#"){
            queue.push([a,b])
          }
        }
      } 
      G[x][y]="#"
    }
  }
  
  
  return -1;
}


```
### Hops
https://www.metacareers.com/profile/coding_puzzles/coding_puzzles?puzzle=977526253003069

A family of frogs in a pond are traveling towards dry land to hibernate. They hope to do so by hopping across a trail of 
�
N lily pads, numbered from 
1
1 to 
�
N in order.
There are 
�
F frogs, numbered from 
1
1 to 
�
F. Frog 
�
i is currently perched atop lily pad 
�
�
P 
i
​
 . No two frogs are currently on the same lily pad. Lily pad 
�
N is right next to the shore, and none of the frogs are initially on lily pad 
�
N.
Each second, one frog may hop along the trail towards lily pad 
�
N. When a frog hops, it moves to the nearest lily pad after its current lily pad which is not currently occupied by another frog (hopping over any other frogs on intermediate lily pads along the way). If this causes it to reach lily pad 
�
N, it will immediately exit onto the shore. Multiple frogs may not simultaneously hop during the same second.
Assuming the frogs work together optimally when deciding which frog should hop during each second, determine the minimum number of seconds required for all 
�
F of them to reach the shore.

```js

function getSecondsRequired(N, F, P) {
  // Write your code here
  //shortest path BFS
  // with a graph of lily status
  var firstFrog =Number.MAX_SAFE_INTEGER
  var lastFrog = 0
  var cnt = 0
  for(var p of P){
    firstFrog = Math.min(p,firstFrog)
    lastFrog = Math.max(p,lastFrog)
    cnt ++
  }
  
  var steps = (lastFrog-firstFrog+(N-lastFrog))
  return steps;
}


```
## Director of Photography (Chapter 1)
https://www.metacareers.com/profile/coding_puzzles/coding_puzzles?puzzle=870874083549040

Note: Chapter 2 is a harder version of this puzzle. The only difference is a larger constraint on 
�
N.
A photography set consists of 
�
N cells in a row, numbered from 
1
1 to 
�
N in order, and can be represented by a string 
�
C of length 
�
N. Each cell 
�
i is one of the following types (indicated by 
�
�
C 
i
​
 , the 
�
ith character of 
�
C):
If 
�
�
C 
i
​
  = “P”, it is allowed to contain a photographer
If 
�
�
C 
i
​
  = “A”, it is allowed to contain an actor
If 
�
�
C 
i
​
  = “B”, it is allowed to contain a backdrop
If 
�
�
C 
i
​
  = “.”, it must be left empty
A photograph consists of a photographer, an actor, and a backdrop, such that each of them is placed in a valid cell, and such that the actor is between the photographer and the backdrop. Such a photograph is considered artistic if the distance between the photographer and the actor is between 
�
X and 
�
Y cells (inclusive), and the distance between the actor and the backdrop is also between 
�
X and 
�
Y cells (inclusive). The distance between cells 
�
i and 
�
j is 
∣
�
−
�
∣
∣i−j∣ (the absolute value of the difference between their indices).
Determine the number of different artistic photographs which could potentially be taken at the set. Two photographs are considered different if they involve a different photographer cell, actor cell, and/or backdrop cell.


```js
function getArtisticPhotographCount(N, C, X, Y) {
  // Write your code here
  // slide window
  var distance = Y-X
  var countItems = (ind,item)=>{
    var curStep = 0;
    var cnt = 0;
    while(curStep<= distance){
      if(!C.charAt(ind))break
      if(C.charAt(ind)==item) cnt++
      ind ++
      curStep ++
    }
    return cnt
  }
  var ans = 0;
  for(var i = 0;i<N-2;i++){
    if(C.charAt(i)=="P"){
      if(i+X<N){
        for(var j =i+X;j<=i+Y;j++){
          if(!C.charAt(j)) break
          if(C.charAt(j)=="A") ans += countItems(j+X,"B")
        }
      }
    }else if(C.charAt(i)=="B"){
        if(i+X<N){
          for(var j = i+X;j<=i+Y;j++){
           if(!C.charAt(j)) break
           if(C.charAt(j)=="A") ans += countItems(j+X,"P")
          }
        }
      }
  }
  
  return ans
  
}


```
## Cafeteria
https://www.metacareers.com/profile/coding_puzzles/coding_puzzles?puzzle=203188678289677 

A cafeteria table consists of a row of 
�
N seats, numbered from 
1
1 to 
�
N from left to right. Social distancing guidelines require that every diner be seated such that 
�
K seats to their left and 
�
K seats to their right (or all the remaining seats to that side if there are fewer than 
�
K) remain empty.
There are currently 
�
M diners seated at the table, the 
�
ith of whom is in seat 
�
�
S 
i
​
 . No two diners are sitting in the same seat, and the social distancing guidelines are satisfied.
Determine the maximum number of additional diners who can potentially sit at the table without social distancing guidelines being violated for any new or existing diners, assuming that the existing diners cannot move and that the additional diners will cooperate to maximize how many of them can sit down.
Please take care to write a solution which runs within the time limit.

```js
function getMaxAdditionalDinersCount(N, K, M, S) {
  var cnt =0;
  var calculateDiner = (left, right)=>{
    var seats = right - left
    var diners = Math.floor(((seats)/(K+1)))-1
    return Math.max(diners,0)
  }
  var sortedSeat = S.sort((a, b) => a - b)
  if(sortedSeat[0]!==1) sortedSeat.unshift(1)
  if(sortedSeat[1]-sortedSeat[0]>K+1) cnt++
  if(sortedSeat[sortedSeat.length-1]!==N) sortedSeat.push(N)
  if(sortedSeat[sortedSeat.length-1]-sortedSeat[sortedSeat.length-2]>K+1) cnt++
  for(var i = 0;i<M+1;i++){
    console.log(sortedSeat[i],sortedSeat[i+1],calculateDiner(sortedSeat[i],sortedSeat[i+1]))
    cnt += calculateDiner(sortedSeat[i],sortedSeat[i+1])
  }
  return cnt;
}


```
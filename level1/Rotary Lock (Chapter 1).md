### Rotary Lock (Chapter 1)
https://www.metacareers.com/profile/coding_puzzles/coding_puzzles?puzzle=990060915068194

You're trying to open a lock. The lock comes with a wheel which has the integers from 
1
1 to 
�
N arranged in a circle in order around it (with integers 
1
1 and 
�
N adjacent to one another). The wheel is initially pointing at 
1
1.
For example, the following depicts the lock for 
�
=
1
0
N=10 (as is presented in the second sample case).

It takes 
1
1 second to rotate the wheel by 
1
1 unit to an adjacent integer in either direction, and it takes no time to select an integer once the wheel is pointing at it.
The lock will open if you enter a certain code. The code consists of a sequence of 
�
M integers, the 
�
ith of which is 
�
�
C 
i
​
 . Determine the minimum number of seconds required to select all 
�
M of the code's integers in order.
Please take care to write a solution which runs within the time limit.

```js

function getMinCodeEntryTime(N, M, C) {
  // Write your code here
  var ans = 0;
  C.unshift(1)
  for(var i =0;i<M;i++){
    var gap = Math.abs(C[i]-C[i+1])
    ans += Math.min(gap,N-gap)
  }
  return ans;
}

```
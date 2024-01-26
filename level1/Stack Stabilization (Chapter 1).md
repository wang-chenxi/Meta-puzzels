### Stack Stabilization (Chapter 1)
https://www.metacareers.com/profile/coding_puzzles/coding_puzzles?puzzle=183894130288005

There's a stack of 
�
N inflatable discs, with the 
�
ith disc from the top having an initial radius of 
�
�
R 
i
​
  inches.
The stack is considered unstable if it includes at least one disc whose radius is larger than or equal to that of the disc directly under it. In other words, for the stack to be stable, each disc must have a strictly smaller radius than that of the disc directly under it.
As long as the stack is unstable, you can repeatedly choose any disc of your choice and deflate it down to have a radius of your choice which is strictly smaller than the disc’s prior radius. The new radius must be a positive integer number of inches.
Determine the minimum number of discs which need to be deflated in order to make the stack stable, if this is possible at all. If it is impossible to stabilize the stack, return 
−
1
−1 instead.

```js

function getMinimumDeflatedDiscCount(N, R) {
  // Write your code here
  var ans = 0;
  for(var i = N-1;i>0;i--){
    if(R[i]<i+1){
      ans = -1
      break
    }
    if(R[i]<=R[i-1]){
      R[i-1] = R[i]-1
      ans ++
    }
  }
  return ans;
}

```
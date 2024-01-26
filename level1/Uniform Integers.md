### Uniform Integers
https://www.metacareers.com/profile/coding_puzzles/coding_puzzles?puzzle=228269118726856

A positive integer is considered uniform if all of its digits are equal. For example, 
2
2
2
222 is uniform, while 
2
2
3
223 is not.
Given two positive integers 
�
A and 
�
B, determine the number of uniform integers between 
�
A and 
�
B, inclusive.
Please take care to write a solution which runs within the time limit.

```js

function getUniformIntegerCountInInterval(A, B) {
  // Write your code here
  //111 3333
  //3333-111 = 3222
  var getUniforms = (n,isA) =>{
    var len = n.toString().length
    var cnt
    cnt = (len-1)*9
    var benchMark = new Array(len).fill(1).join("")
    cnt += Math.floor(n/benchMark)
    if(isA&&n%benchMark==0) cnt-=1
    return cnt
  }
  return getUniforms(B,false)-getUniforms(A,true)
}

```
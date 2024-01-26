### Scoreboard Inference (Chapter 1)
https://www.metacareers.com/profile/coding_puzzles/coding_puzzles?puzzle=348371419980095

Note: Chapter 2 is a harder version of this puzzle. The only difference is a larger set of possible problem point values.
You are spectating a programming contest with 
�
N competitors, each trying to independently solve the same set of programming problems. Each problem has a point value, which is either 1 or 2.
On the scoreboard, you observe that the 
�
ith competitor has attained a score of 
�
�
S 
i
​
 , which is a positive integer equal to the sum of the point values of all the problems they have solved.
The scoreboard does not display the number of problems in the contest, nor their point values. Using the information available, you would like to determine the minimum possible number of problems in the contest.

```js
function getMinProblemCount(N, S) {
  // Write your code here
  var score_1 = 0;
  var score_2 = 0;
  for(var i = 0;i<N;i++){
    if(S[i]%2==1) score_1 = 1
    if(score_1+(2*score_2)<S[i]){
      var x = S[i]%2
      var y = Math.floor(S[i]/2)
      score_2 = Math.max(score_2,y)
    }
  }
  return score_1+score_2;
}

```
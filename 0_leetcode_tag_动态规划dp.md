- offer 62. 圆圈最后的数字

  ```c++
  class Solution {
  public:
      int lastRemaining(int n, int m) {
          vector<int> dp(n,0);//dp[0] has no meaning
          dp[1] = m%2;
          //calculate dp
          for(int i=2; i<n;i++){
              dp[i] = ((m%(i+1)) + dp[i-1])%(i+1); //还是有点秀的
          }
          return dp[n-1];
      }
  };
  ```

  


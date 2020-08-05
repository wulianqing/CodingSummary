# 位运算



- Acwing 801. 二进制中1的个数

	```c++
	//主要操作
	while(num!=0){
		if(num & 1)counter++; //num & 1即num最后一位
 	 num >>= 1; //右移1位
	}
	```

- offer 65. 位运算两数相加

  ```c++
  class Solution {
  public:
      int add(int a, int b) {
          int ans;
          int carry;  
          //其实是把ans和carry转换成a和b相加缩小问题范围
          while(b!=0){
              ans = a ^ b;
              carry = (unsigned int)(a & b)<<1;   
              a = ans;
              b = carry;
          }
          return a;
      }
  };
  ```

- 美团2020第2题. 汉明距离(同理)

  ```c++
  #include <iostream>
  
  int HammingDistance(int a,int b){
      int big, small;
      int counter=0;
      if (a > b)
      {
          big = a;
          small = b;
      }
      else{
          big = b;
          small = a;
      }
      while(big!=0){
          if((big&1)^(small&1))
              counter++;
          big >>= 1;
          small >>= 1;
      }
      return counter;
  }
  
  int main(){
      int max_distance=0;
      int num_count;
      std::cin >> num_count;
      if(num_count== 0 || num_count == 1)
          std::cout << 0 << std::endl;
      int nums[num_count];
      for (int i = 0; i < num_count;i++){
          std::cin >> nums[i];
      }
      for (int i = 0; i < num_count;i++){
          for (int j = i + 1; j < num_count;j++){
              if(HammingDistance(nums[i],nums[j])>max_distance)
                  max_distance = HammingDistance(nums[i], nums[j]);
          }
      }
      std::cout << max_distance << std::endl;
      return 0;
  }
  ```

- offer 16.快速幂 

  ```c++
  //quick product
  while(exp_num != 1){
    if((exp_num & 1) == 1)
      ans *= base_num; //指数为奇数,需要单独先保存在ans
    base_num *= base_num;       
  	exp_num /= 2;
  }
  ans *= base_num;
  ```

- offer 56-I.  数组中有2个只出现1次的数字 其他均为2次

  ```c++
  class Solution {
  public:
      vector<int> singleNumbers(vector<int>& nums) {
          int mixed = 0;
          for(int num:nums){
              mixed ^= num;
          }
          int mask = 1;
        	//注意&的运算优先级低于==,要加()
          while((mixed & mask) == 0)
            mask<<=1;//找低位1,即两个位不同的位
          int first_elem = 0;
          int second_elem = 0;
        	//从头再来一遍,分开
          for(int num:nums){
              if(mask & num)
                  first_elem ^= num;
              else
                  second_elem ^= num;
          }
          return vector<int>{first_elem,second_elem};
      }
  };
  
```
  
  
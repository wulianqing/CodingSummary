Link：[CSDN-C++字符串及基本操作](https://blog.csdn.net/weixin_43930512/article/details/91041396)



string

1. 头文件:<string>

2. 赋值
   1. 初始化赋值：`string s = "abc";`
   2. `cin >> s`：以空格，换行符，tab键作为结束标志
   3. `getline(cin,s);`：以换行符为结束标志

3. 常用操作

   ```c++
   //获取第i个字符
   s[i];
   s.at(1);
   
   //长度
   s.size();
   s.length();
   
   //查找t是否为s的字串
   s.find(t); //返回第一次出现的位置
   
   //char[]转为string
   s = str;
   //string转为char[]：则需要逐个赋值 ！！！
   
   //两个string连接
   s1 = s1 + s1;
   s1.append(s2);
   
   //对比
   s1<s2;
   s1.compare(s2);
   ```

   
   
   ```c++
   //string初始化
   string str1("abcd");
   string str2(5, 'a');  //5个a
   string str3("abcdefghijk",3);   //abc
   string str4 ( "abcdefghijk",3,5);   //从第三个位置开始取5个字符
   string s1="abc";
   
   string类常见操作：
     1.增加：+, append, insert, push_back
     2.删除：clear, pop_back, erase
     3.修改：replace, assign, swap
     4.大小：size, length, capacity, max_size, resize, reserve
   	5.判断：empty, compare, >=, <=, >, <
   	6.遍历：begin, end, front, back, at, find
   	7.其他：getline, string转换, substr
   
     1. 增加
     	1. +
     	2. append：vector没有的操作。
     			s1.append(s2);   //不能用a1.append("def")
   				s1.append(3,'K'); //3个'K'
   				s1.append(s2,1,2);//增加s2从1位开始的两位字符
   		3. insert
   				s1.insert(2,"def"); 
   				s1.insert(2,s2,1,2); //插入s2的1位开始的两个字符
   				s1.insert(2,s2);
   				s1.insert(s1.begin(),'1');
   				s1.insert(s1.begin(),3,'1');
   
   	2. 删除/置换 同理
       1. erase
       2. replace
       
     3. 比较 *
       1. compare
   				string s("abcd");
   				s.compare("abcd"); //返回0
   				s.compare("dcba"); //返回一个小于0的值
   				s.compare("ab"); //返回大于0的值
   				s.compare(s); //相等
   				s.compare(0,2,s,2,2); //用"ab"和"cd"进行比较 小于零
   				s.compare(1,2,"bcx",2); //用"bc"和"bc"比较，起始默认0
   		2. 使用<, >
   				s1 > s2; //s1="abcd",s2="real"
   
   	4. 搜索遍历
       1. find, rfind,find_last_of,find_last_of
   				string str="1234eqsabababcdefg";
   				//find
   				str.find("ab");//返回字符串 ab 在 str 的位置
   				str.find("ab", 2);//往后搜索，在 str[2]~str[n-1] 范围内查找并返回字符串 ab 在 str 的位置
   				str.rfind("ab", 2);//往前搜索，在 str[0]~str[2] 范围内查找并返回字符串 ab 在 str 的位置
   				//find_first_of()
   				str.find_first_of("ab");//ab任一字符出现首位置
   				str.find_first_of("ab", 2);//返回ab中任何一个字符首次在 str[2]~str[n-1] 范围中出现的位置
   				//find_last_of()
   				str.find_last_of("23");//返回23中任何一个字符最后一次在 str 中出现的位置
   				str.find_last_of("23", 2);//返回23中任何一个字符最后一次在 str[0]~str[2] 范围中出现的位置
   
   	5. 其他
       1. substr
    	   		string s="abcdefg";
   				string s1=s.substr(1,3);   //bcd,第一个参数表示起始位置, 第二个参数表示长度
   				string s2=s.substr(4);     //efg，(s[4],s[end])
   		2. int和string之间的转换
         	//int -> string 很容易实现，to_string()即可
         	int c = 123;
       		string d = to_string(c); //d:"123"
   
   				//string -> int需要两步，string -> char* -> int
   				//string -> char*使用c_str; char* -> int使用atoi
   				string a = "1234";
      	 		int b = atoi(a.c_str()); //b:1234
   				
   				好像可以直接stoi(a)
   		
   
   ```
   
   


char

1. 头文件

   `<cstring>` 或者 `<string.h>`

2. 赋值

   `char str[] = {'1','2','a','\0'}; //以结束标志符结尾`

   `char str = "12a0"; //系统自动匹配结束标志符`

3. 常用操作

   ```c++
   strlen(str); //长度，不能用.length()或.size()
   strcpy(str1, str2); //复制
   strcat(str1, str2); //拼接
strcmp(str1, str2)；//对比
   ```

   
   
   


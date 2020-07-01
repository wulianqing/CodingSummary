O(logn)

偶数: 

`return Fibonacci[n]=(get_Fibonacci(n/2)*get_Fibonacci(n/2)+get_Fibonacci(n/2-1)*get_Fibonacci(n/2-1));`

奇数:

`else return Fibonacci[n]=(get_Fibonacci(n/2)*get_Fibonacci(n/2+1)+get_Fibonacci(n/2-1)*get_Fibonacci(n/2));`

例如:

F(8)=F(4)F(4)+F(3)F(3)=25+9=34

F(7)=F(3)F(4)+F(2)F(3)=15+6=21
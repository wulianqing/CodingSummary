1. Vector作为函数的**参数或者返回值**时，需要注意它的写法：
   ```double Distance(vector<int>& a, vector<int>& b) ```
   
   其中的“&”绝对不能少！！！



2. 向量长度较长，容易导致内存泄漏，而且效率会很低
  
1. **头文件**：`#include<vector>`
  
2. **创建vector对象**：`vector<int> vec`

3. **尾部插入数字**：`vec.push_back(a)`

4. 使用**下标访问**元素：`cout<<vec[0]<<endl`记住下标是从0开始的。

5. 使用**迭代器**访问元素.
    ```c++
    vector<int>::iterator it;
    for(it=vec.begin();it!=vec.end();it++)
    cout<<*it<<endl;
    ```
	
    
    
6. **插入元素**：`vec.insert(vec.begin()+i,a);`  在第i+1个元素前面插入a
    比如`vec.begin()+3, a`表示在vec[3]前插a
    
7. **删除元素**：`vec.erase(vec.begin()+2);`删除第3个元素 	 
    比如`vec.begin()+3`, 则删除vec[3]::
    `vec.erase(vec.begin()+i,vec.end()+j);`删除区间[i,j);区间从0开始  注意 左闭右开	
    //与上面是统一的第j个=vec[j-1]
  
8. **向量大小**：`vec.size();`
  
9. **清空**：`vec.clear();`


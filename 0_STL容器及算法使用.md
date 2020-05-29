- 序列容器

  - vector

    ```c++
    vector<int> v;
    v.push_back(1);
    v.insert(v.begin()+i,a);//在v[i]前插入a,使a成为v[i]
    v.erase(v.begin()+i);//删除v[i]
    v.erase(v.begin()+i,v.begin()+j);//删除[i,j) 左闭右开
    ```

  - List

  - Deque

- 关联容器

  - set

    ```c++
    #include<set>
    set<int> my_set;
    my_set.begin();
    my_set.end();
    my_set.count(x);//x的个数
    my_set.erase(it);//iterator
    my_set.erase(x);//删除值为x
    my_set.erase(first,second);//元素[first,second)
    
    ```

  - Multi_set

  - Map

    ```c++
    unordered_map<int,string> my_map;
    my_map.insert(make_pair(1,"abc"));
    my_map[2] = "def";
    my_map[2]; //"def"
    my_map.find(2); //iterator
    ```

  - Multi_map

- 容器适配器

  - stack

    ```c++
  push();
    pop();
  top();
    ```
  
  - queue
  
  ```c++
    front();
    back();
    push();
    pop();
    ```
  
  - priority_queue(最大/小堆)
  
    ```c++
    priority_queue<int,vector<int>,less<int>> q;最大堆（默认为最大堆）
    priority_queue<int,vector<int>,greater<int>> q;最小堆
      
    priority_queue<int>
    push();
    top();
    pop();
    ```
  
    


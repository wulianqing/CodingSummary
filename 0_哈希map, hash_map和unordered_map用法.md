1. map与vector_map(vector_map c++没有提供实现)

   1. map

      1. 构造函数

      ```c++
      map<string,int> mapstring;         
      map<int,string > mapint;
      map<string,char> mapstring;         
      map<char,string> mapchar;
      map<char,int> mapchar;            
      map<int,char> mapint；
      ```

      2. 添加数据

      ```c++
      map<int ,string> maplive;  
      maplive.insert(pair<int,string>(102,"aclive"));
      maplive.insert(map<int,string>::value_type(321,"hai"));
      maplive[112]="April"; //map中最简单最常用的插入添加！
      ```

      3. 元素查找（find返回的是一个iterator，不管查找/删除都是对iterator操作）

      ```c++
      map<int ,string >::iterator l_it;
      l_it=maplive.find(100);
      if(l_it==maplive.end()){
        return false; 
      }
      else return l_it; 
      ```

      4. 元素删除

      ```c++
      map<int ,string >::iterator l_it;;   
      l_it=maplive.find(100);
      if(l_it==maplive.end()) return false;
      else  maplive.erase(l_it);  //delete 100;
      ```

      5.  swap用法（交换的是容器，而不是容器中的的元素）

      ```c++
      m1.swap( m2 );
      ```

      6. **map的sort问题**：Map中的元素是自动按key升序排序，所以不能对map用sort函数
      7. map基本操作

      ```c++
      begin();          //返回指向map头部的迭代器*
      clear();          //删除所有元素
      count();          //返回指定元素出现的次数*
      empty();          //如果map为空则返回true
      end();            //返回指向map末尾的迭代器*
      equal_range();    // 返回特殊条目的迭代器对
      erase();          //删除一个元素*
      find();           //查找一个元素*
      get_allocator();  //返回map的配置器
      insert();         //插入元素*
      key_comp();       //返回比较元素key的函数
      lower_bound();    //返回键值>=给定元素的第一个位置
      max_size();       //返回可以容纳的最大元素个数
      rbegin();         //返回一个指向map尾部的逆向迭代器
      rend();           //返回一个指向map头部的逆向迭代器
      size();           //返回map中元素的个数*
      swap();           //交换两个map*
      upper_bound();    //返回键值>给定元素的第一个位置
      value_comp();     //返回比较元素value的函数
      ```

      

查找时间：O(lg(n))～O(2*log(n))。map使用**红黑树**实现，**构建map花费的时间比较长**，因而map适用于那种**插入和查询混合**的情况。

如果是**先插入后查询**的情况，可以考虑使用vector_map.vector_map在C＋＋中没有实现，想使用可以自己实现。其基本思想在于使用vector来保存数据，**插入完成后进行排序，然后使用二分查找进行查询**。这样在先插入后查询的条件下，性能会比map好很多。原因主要在几个方面：

1. **vector使用线性存储 map是二叉树形状**，所以vector的局部性更好。
2. vector可以一次分配很大的内存，而map需要每次分配一个节点，而且map中相对于vector有很多冗余数据，比如指向子节点的指针。
3. vector是**插入完成后统一进行排序**，而**map每次insert都有一次查找和树的旋转**。
4. vector_map是**二分查找，查找时间稳定在O(lg(n))**，而map的存储结构是**红黑树，查找时间为O(lg(n))-O(2*log(n))**。

```c++
#include <iostream>
#include <map>	//头文件
using namespace std;
 
typedef std::map<int, string> Map;	//std::map<int,string>
typedef Map::iterator MapIt;//迭代器 
 
int main()
{
    Map *map = new Map();
    int key;
    string value;
    while(cin>>key>>value)
    {
        map->insert(make_pair(key, value));//make_pair()
    }
    for(MapIt it = map->begin(); it != map->end(); ++it)	//++it(Map::interator)
        cout<<"key:"<<it->first<<" value:"<<it->second<<endl;
    delete map;
    return 0;
}
```



2. hash_map

STL中的实现叫做unordered_map，都是基于hash_table实现的。首先，分配一大片内存，形成很多桶。利用hash函数，将key映射到不同的桶中，也有可能会有两个不同的key映射到同一个桶中，这时就需要判别函数来进行查找了。所以hash_map的key需要两个条件，一个是**hash函数**，获得映射到的桶的值，另外一个是**equal_to函数**，判定两个key是否相等。显然，当**每个桶里的元素个数比较平均且比较少**的时候，查询性能比较高。

```c++
//常用语法
#include <unordered_map>

std::hash_map<int,string> my_map;
my_map[4] = "(string)";
my_map.insert(make_pair(int,string));
my_map.find(int);
my_map.begin();
my_map.end();//均返回整个结构 这个结构类型是std::hash_map<int,string>::iterator
if(my_map.find(4)!=my_map.end()) //key=4的项存在
cout<<my_map[4]<<endl;
std::hash_map<int,string>::iterator it;
it = my_map.find(int);
cout<<it->first<<"	"<<it->second<<endl

```


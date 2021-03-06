# MakeData.h

一个用于生成数据的库

## Srand(ull seed)

初始化随机数,默认为 `seed=time(NULL)`.

## Bgein()

开始生成一个数据,其中包含 `Sleep(1000)`(防止相邻数据的随机化种子相同)以及初始化随机数.

## Random(ll a)

等概率随机生成一个 ![](https://latex.codecogs.com/svg.latex?[0,a%29) 内的整数.

## Random(ll l,ll r)

等概率随机生成一个 ![](https://latex.codecogs.com/svg.latex?[l,r]) 内的整数.

## RandomChar(char l,char r)

随机返回一个在 ![](https://latex.codecogs.com/svg.latex?l) 到 ![](https://latex.codecogs.com/svg.latex?r) 范围内的字符.

其中包含以下可用的宏定义:

```cpp
#define _abc_ 'a','z'//小写字母
#define _ABC_ 'A','Z'//大写字母
#define NUM '0','9'//数字
#define CHAR 32,126//可见字符
```

~~虽然这个东西和 `Random(ll l,ll r)` 一毛一样.~~

## RandomChar(char \*s)

随机返回字符串 ![](https://latex.codecogs.com/svg.latex?s) 中的一个字符.

其中如果 `s="abb"`,那么返回的元素出现 `a` 的概率为 ![](https://latex.codecogs.com/svg.latex?\frac{1}{3}),出现 `b` 的概率为 ![](https://latex.codecogs.com/svg.latex?\frac{2}{3}).

## MakeArray(ll/int \*array,int l,int r,ll/int num_l,ll/int num_r)

对于 ![](https://latex.codecogs.com/svg.latex?array_l\sim%20array_r) 中的元素随机给出一个 ![](https://latex.codecogs.com/svg.latex?[num\_l,num\_r]) 范围内的整数.

## MakeArray(ll/int \*array,int n,ll/int num_l,ll/int num_r)

相当于 `MakeArray(array,1,n,num_l,num_r)`.

## MakeArray(ll/int \*array,int l,int r,ll/int(\*MakeNum)())

对于 ![](https://latex.codecogs.com/svg.latex?array_l\sim%20array_r) 中的元素都用 `MakeNum()` 赋值一次.

## MakeArray(ll/int \*array,int n,ll(\*MakeNum)())

相当于 `MakeArray(array,1,n,MakeNum())`.

## MakeArray(int \*array,int n)

对于 ![](https://latex.codecogs.com/svg.latex?array_1\sim%20array_n) 中的元素随机给出一个 ![](https://latex.codecogs.com/svg.latex?1\sim%20n) 的排列(![](https://latex.codecogs.com/svg.latex?1\sim%20n) 中每个元素有且出现一次但是没有顺序).

## MakeString(char \*s,int l,int r,char \*t)

对于 ![](https://latex.codecogs.com/svg.latex?s_l\sim%20s_r) 中的元素都等概率随机给出 `t[]` 中的元素.

其中如果 `t="abb"`,那么对于 ![](https://latex.codecogs.com/svg.latex?s) 中的每个元素出现 `a` 的概率为 ![](https://latex.codecogs.com/svg.latex?\frac{1}{3}),出现 `b` 的概率为 ![](https://latex.codecogs.com/svg.latex?\frac{2}{3}).

## MakeString(char \*s,int len,char \*t)

相当于 `MakeString(s,0,len-1,char t[])`.

## MakeRange(ll/int &l,ll/int &r,ll/int range_l,ll/int range_r)

将 ![](https://latex.codecogs.com/svg.latex?l,r) 变成 ![](https://latex.codecogs.com/svg.latex?[range\_l,range\_r]) 内的随机一个整数,且严格保证 ![](https://latex.codecogs.com/svg.latex?l\leq%20r).

## WriteArray(ll/int \*array,int l,int r,char s[2])

输出 ![](https://latex.codecogs.com/svg.latex?array_l\sim%20array_r),其中对于 ![](https://latex.codecogs.com/svg.latex?array_l\sim%20array_{r-1}) 后会输出 `s[0]`,![](https://latex.codecogs.com/svg.latex?array_r) 后会输出 `s[1]`.

## WriteArray(ll/int \*array,int n,char s[2])

相当于 `WriteArray(array,1,n,s)`.

其中 ![](https://latex.codecogs.com/svg.latex?s) 的默认值是 `" \n"`,即在一行内输出 ![](https://latex.codecogs.com/svg.latex?array_l\sim%20array_r) 用空格隔开,并且在最后换行.

## struct Graph

一个用于存储图的结构体.

构造函数 `Graph(n,l)`,其中 ![](https://latex.codecogs.com/svg.latex?n) 为节点个数编号为 ![](https://latex.codecogs.com/svg.latex?1\sim%20n),![](https://latex.codecogs.com/svg.latex?l) 是否为有向图(![](https://latex.codecogs.com/svg.latex?l=0) 为有向图,![](https://latex.codecogs.com/svg.latex?l=1) 为无向图).

### Graph.AddEdge(int a,int b)

添加一条连接 ![](https://latex.codecogs.com/svg.latex?a,b) 的边.

### Clean()

清空图.

对于此结构体包含以下 `define`:

```cpp
#define FOR(edge,now) for(int edge_i=0,to=edge.out_point[now].size()?edge.out_point[now][0]:0;edge_i<edge.out_point[now].size();edge_i++,to=edge.out_point[now][edge_i])
/*
FOR(e,a) 表示在遍历 e 这个图中 a 的出边,其中 to 表示连出的节点的编号
*/
```
## MakeTree(Graph &a,int n,int root,bool link,int opt,int k)

其中 ![](https://latex.codecogs.com/svg.latex?root) 默认为 ![](https://latex.codecogs.com/svg.latex?1),![](https://latex.codecogs.com/svg.latex?link) 默认为 ![](https://latex.codecogs.com/svg.latex?0),![](https://latex.codecogs.com/svg.latex?opt) 默认为 ![](https://latex.codecogs.com/svg.latex?0),![](https://latex.codecogs.com/svg.latex?k) 默认为 ![](https://latex.codecogs.com/svg.latex?2).

![](https://latex.codecogs.com/svg.latex?a) 表示要生成的树所存储的图,![](https://latex.codecogs.com/svg.latex?n) 表示有 ![](https://latex.codecogs.com/svg.latex?n) 个节点,![](https://latex.codecogs.com/svg.latex?root) 表示根节点编号,![](https://latex.codecogs.com/svg.latex?link) 表示十分是无向图(![](https://latex.codecogs.com/svg.latex?link=0) 是有向图,只有父亲向儿子连边,![](https://latex.codecogs.com/svg.latex?link=1) 是无向图),![](https://latex.codecogs.com/svg.latex?opt) 表示生成树的种类,![](https://latex.codecogs.com/svg.latex?k) 是辅助用数.

![](https://latex.codecogs.com/svg.latex?opt):

0. 生成一颗随机的树.
1. 生成一条随机的链.
2. 生成一个随机的菊花图(根节点出度为 ![](https://latex.codecogs.com/svg.latex?n-1)).
3. 生成一个随机的 ![](https://latex.codecogs.com/svg.latex?k) 叉树(每个点的儿子个数最多为 ![](https://latex.codecogs.com/svg.latex?k)).
4. 生成一个随机的满二叉树.

## MakeGraph(Graph &gra,int n,int m,bool connect,bool link,int opt)

其中 ![](https://latex.codecogs.com/svg.latex?connect) 默认值为 ![](https://latex.codecogs.com/svg.latex?0),![](https://latex.codecogs.com/svg.latex?link) 默认为 ![](https://latex.codecogs.com/svg.latex?0),![](https://latex.codecogs.com/svg.latex?opt) 默认为 ![](https://latex.codecogs.com/svg.latex?0).

![](https://latex.codecogs.com/svg.latex?a) 表示要生成的图所存储的图,![](https://latex.codecogs.com/svg.latex?n) 表示有 ![](https://latex.codecogs.com/svg.latex?n) 个节点,![](https://latex.codecogs.com/svg.latex?m) 表示有 ![](https://latex.codecogs.com/svg.latex?m) 条边,![](https://latex.codecogs.com/svg.latex?connect) 表示是否连通(![](https://latex.codecogs.com/svg.latex?connect=0) 表示不一定连通,![](https://latex.codecogs.com/svg.latex?connect=1) 表示连通,即每个点都可以到所有其他的点),![](https://latex.codecogs.com/svg.latex?link) 表示是否是无向图(![](https://latex.codecogs.com/svg.latex?link=0) 是有向图,![](https://latex.codecogs.com/svg.latex?link=1) 是无向图),![](https://latex.codecogs.com/svg.latex?opt) 表示生成图的种类.

![](https://latex.codecogs.com/svg.latex?opt):

0. 一个随机的图.

## void WriteGraph(Graph &a)

输出图 ![](https://latex.codecogs.com/svg.latex?a),如果 ![](https://latex.codecogs.com/svg.latex?a) 是有向图每条边 ![](https://latex.codecogs.com/svg.latex?u\to%20v) 都会输出一次,如果 ![](https://latex.codecogs.com/svg.latex?a) 是无向图,![](https://latex.codecogs.com/svg.latex?u\leftrightarrow%20v) 只会出现一次(`u v` 和 `v u` 都有概率出现)


# make.bat

一个可以和 makedata.h 一起使用的批处理文件.

## 使用方法

makedata.exe,std.exe,make.bat 放在同一目录下,并运行 bat 文件,其中的 ![](https://latex.codecogs.com/svg.latex?l) 和 ![](https://latex.codecogs.com/svg.latex?r) 为数据的编号范围 ![](https://latex.codecogs.com/svg.latex?l.cpp\sim%20r.cpp).

其中的 std 和 makedata 都不需要读入输出文件.

# 近期推出(完善)

各种图和树.

欢迎联系 QQ2303504461 提出建议.

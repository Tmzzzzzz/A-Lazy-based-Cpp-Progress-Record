# 部分函数总览

* Algorithm
  - `sort()`
  - `reverse()`
  - `unique()`
  - `swap()`
  - `max()` / `min()`
  - `lower_bound()` / `upper_bound()`
* cmath
  - `abs()` 绝对值
  - `sqrt()` 平方根
  - `pow(a,b)` 幂(a的b次方)
  - `exp(x)` 指数(e的x次方)
  - `log()` / `log10()` 对数
  - `ceil()` / `floor()` 向上/向下取整（浮点数）
  - `round()` (C++11) 四舍五入到整数
* numeric
  - `gcd()` (C++17)
  - `lcm()` (C++17)


## 1. swap()
`swap(a,b)` 

交换a和b的值（可以是整数、浮点数或其他可交换的类型）

## 2. sort()
`sort(a.begin(),a.end(),比较器)` 

对容器/数组 a 的区间 [begin,end) 内的元素进行排序，默认使用 `greater<>()` 升序排序。

可以自行定义`bool compare(类型 a, 类型 b)` 作为比较器。从大到小排序`return a>b`

## 3. lower_bound() / upper_bound()
在 **已升序排序** 范围内进行 **二分查找**，找不到则返回 **尾迭代器**

`lower_bound(a.begin(), a.end(), x)` 返回第一个 `>= x` 的元素的迭代器。

`upper_bound(a.begin(), a.end(), x)` 返回第一个 `> x` 的元素的迭代器。

## 4. reverse()

`reverse(a.begin(),a.end())`

**反转**容器/数组 a 的区间 [begin,end) 内的元素。

## 5. max() / min()
比较两个变量的大小

（比较多个变量用套娃或者 `min({})` / `max({})`）

## 6. unique()
`unique(a.begin(), a.end())`

**消除相邻重复元素**，数组长度不变，有效数据缩短，返回**有效数据末尾的迭代器**

例： $[1,1,4,5,1,4]$ -> $[1,4,5,1,4,?]$

* 若要达到**去重**效果，可以在 `unique()` 后调用 `erase()` ：

    ```cpp
    vector<int> a={...}
    sort(a.begin(), a.end());
    a.erase(unique(a.begin(), a.end()), a.end());
    ```
## 7. gcd() / lcm() (C++17)
返回最大公因数/最小公倍数

若不支持C++17，手动实现：
```cpp
int gcd(int a,int b){
    if(!b)return a;
    return gcd(b , a % b)
}

int lcm(int a,int b){
    return a / gcd(a,b) * b;
}
```

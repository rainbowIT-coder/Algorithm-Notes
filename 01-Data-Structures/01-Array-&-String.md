# 数组和字符串
## 1.遍历数组
- 用for循环遍历
```cpp
// 遍历数组
for (int i = 0; i < arr_size; i++) {
    cout << arr[i] << " ";
}

// 遍历字符串 (C++ std::string)
string s = "Hello";
for (int i = 0; i < s.length(); i++) {
    cout << s[i] << " ";
}
```
- 用for-each循环遍历
```cpp
//数组
for(int element:arr)
{
    cout<<element<<" ";
    // 对于数组arr中的每个元素element
}

//字符串
for(int c:s)
{
    cout<<c<<" ";
    // 对于字符串s中的每个字符c
}
for(auto &c:s) // 如果想要改变 string 对象中的值，必须把循环变量定义为引用类型 
   c=toupper(c); // 若c是大写字母，转换为小写输出，否则原样输出
cout<<s1<<endl;
```
## 2.内置方法
### 字符串(string)
- **定义**
  使用标准库类型 string 声明并初始化一个字符串，需要包含头文件 string。可以初始化的方式如下：

```cpp
      string s1;    // 初始化一个空字符串
    string s2 = s1;   // 初始化s2，并用s1初始化
    string s3(s2);    // 作用同上
    string s4 = "hello world";   // 用 "hello world" 初始化 s4，除了最后的空字符外其他都拷贝到s4中
    string s5("hello world");    // 作用同上
    string s6(6,'a');  // 初始化s6为：aaaaaa
    string s7(s6, 3);  // s7 是从 s6 的下标 3 开始的字符拷贝
    string s8(s6, pos, len);  // s7 是从 s6 的下标 pos 开始的 len 个字符的拷贝
```
- **读写操作**
输入时遇到空格或回车键将停止。但需要注意的是只有按下回车键时才会结束输入执行，当按下空格后还能继续输入，但最终存到字符串中的只是第一个空格之前输入的字符串（开头的空白除外，程序会自动忽略开头的空白的），空格操作可以用来同时对多个字符串进行初始化。例如：
```cpp
#include <iostream>
#include <string>
using namespace std;
int main(void)
{
    string s1, s2, s3;    // 初始化一个空字符串
    // 单字符串输入，读入字符串，遇到空格或回车停止
    cin >> s1;  
    // 多字符串的输入，遇到空格代表当前字符串赋值完成，转到下个字符串赋值，回车停止
    cin >> s2 >> s3;  
    // 输出字符串 
    cout << s1 << endl; 
    cout << s2 << endl;
    cout << s3 << endl;   
    return 0;
}
// 运行结果 //
  abc def hig
abc
def
hig
```
如果希望在最终读入的字符串中保留空格，可以使用 getline 函数，例子如下：

```cpp
#include <iostream>
#include <string>
 
using namespace std;
 
int main(void)
{
    string s1 ;    // 初始化一个空字符串
    getline(cin , s1); 
    cout << s1 << endl;  // 输出
    return 0;
}
// 结果输出 //
abc def hi
abc def hi
```


- **常用功能**
  
| 函数 | 说明 |
|------|------|
| s.insert(pos, args) | 在 pos 之前插入 args 指定的字符 |
| s.erase(pos, len) | 删除从 pos 开始的 len 个字符。如果 len 省略，则删除 pos 开始的后面所有字符。返回一个指向 s 的引用。 |
| s.assign(args) | 将 s 中的字符替换为 args 指定的字符。返回一个指向 s 的引用。 |
| s.append(args) | 将 args 追加到 s。返回一个指向 s 的引用。args 必须是双引号字符串 |
| s.replace(range, args) | 将 s 中范围为 range 内的字符替换为 args 指定的字符 |
| s.find(args) | 查找 s 中 args 第一次出现的位置 |
| s.rfind(args) | 查找 s 中 args 最后一次出现的位置 |
| to_string(val) | 将数值 val 转换为 string 并返回。val 可以是任何算术类型（int、浮点型等） |
| stol(s) / atol(c) | 字符串/字符串 转换为整数并返回 |
| stof(s) / atof(s) | 字符串/字符串 转换为浮点数并返回 |
| s.substr(pos, n) | 从索引 pos 开始，提取连续的 n 个字符，包括 pos 位置的字符 |
| reverse(s2.begin(), s2.end()) | 反转 string 定义的字符串 s2（加头文件 <algorithm>） |

代码示例：
```cpp
#include <iostream>
#include <string>
using namespace std;
int main(void)
{
//查询字符串信息、索引
    string s1 = "abc";    // 初始化一个字符串
    cout << s1.empty() << endl;  // s 为空返回 true，否则返回 false
    cout << s1.size() << endl;   // 返回 s 中字符个数，不包含空字符
    cout << s1.length() << endl;   // 作用同上
    cout << s1[1] << endl;  // 字符串本质是字符数组
    cout << s1[3] << endl;  // 空字符还是存在的
    return 0;

//拼接、比较等操作（cctype 头文件(判断字符类型：大/小写字母、标点、数字等)）
isalnum(c)  // 当是字母或数字时为真
isalpha(c)  // 当是字母时为真
isdigit(c)  // 当是数字是为真
islower(c)  // 当是小写字母时为真
isupper(c)  // 当是大写字母时为真
isspace(c)  // 当是空白（空格、回车、换行、制表符等）时为真
isxdigit(c) // 当是16进制数字是为真
ispunct(c)  // 当是标点符号时为真（即c不是 控制字符、数字、字母、可打印空白 中的一种）
isprint(c)  // 当时可打印字符时为真（即c是空格或具有可见形式）
isgraph(c)  // 当不是空格但可打印时为真
iscntrl(c)  // 当是控制字符时为真
tolower(c)  // 若c是大写字母，转换为小写输出，否则原样输出
toupper(c)  // 类似上面的

//搜素操作（搜索操作返回指定字符出现的下标，如果未找到返回 npos ）
s.find(args)  // 查找 s 中 args 第一次出现的位置
s.rfind(args)  // 查找 s 中 args 最后一次出现的位置
s.find_first_of(args)  // 在 s 中查找 args 中任何一个字符最早出现的位置
s.find_last_of(args)  // 在 s 中查找 args 中任何一个字符最晚出现的位置

string s1 = "nice to meet you~"; 
cout << s1.find_first_of("mey") << endl; // 输出结果为 3，'e' 出现的最早
s.find_first_not_of(args)  // 查找 s 中 第一个不在 args 中的字符的位置
s.find_last_not_of(args)  // 查找 s 中 最后一个不在 args 中的字符的位置

string s1 = "nice to meet you~";  
cout << s1.find_first_not_of("nop") << endl; // 输出结果为 1 ，'i' 不在 "nop" 里

//字符串的反转（使用 <algorithm> 头文件中的 reverse() 方法）
string s2 = "12345";    // 初始化一个字符串
reverse(s2.begin(), s2.end()); // 反转 string 定义的字符串 s2 
cout << s2 << endl; // 输出 54321
}


```
————————————————
版权声明：字符串部分基于CSDN博主「地球被支点撬走啦」的原创文章（其中还有string、char 型与数值的转换说明）
原文链接：https://blog.csdn.net/Flag_ing/article/details/123361432
### 动态数组(vector)
- **常用操作**
  
| 函数 | 说明 |
|------|------|
| v.push_back(value) | 在向量末尾添加一个元素（最常用） |
| v.pop_back() | 删除向量末尾的元素 |
| v.size() | 返回向量中元素的个数（非常常用） |
| v.empty() | 检查向量是否为空，为空返回true，否则返回false |
| v.clear() | 删除向量中的所有元素 |
| v.resize(n) | 调整向量大小为n，新增元素默认初始化 |
| v.front() | 返回第一个元素的引用 |
| v.back() | 返回最后一个元素的引用（常用） |
| v.begin() | 返回指向第一个元素的迭代器（用于遍历） |
| v.end() | 返回指向最后一个元素之后位置的迭代器（用于遍历） |
| v[index] | 返回指定位置index处元素的引用（常用，不进行边界检查） |
| v.at(index) | 返回指定位置index处元素的引用，进行边界检查（更安全） |
| v.insert(pos, value) | 在迭代器pos指定位置前插入一个元素value |
| v.erase(pos) | 删除迭代器pos指定位置的元素 |
| std::sort(v.begin(), v.end()) | 对向量中的元素进行排序（需包含<algorithm>，非常常用） |
| std::reverse(v.begin(), v.end()) | 反转向量中的元素顺序（需包含<algorithm>） |

代码示例：
```cpp
#include <iostream>
#include <vector>
#include <algorithm>
using namespace std;
//遍历函数
void print(vector<int> v)
{
	for (int c : v)
	{
		cout << c << " ";
	}
}
int main()
{
	vector<int>v;//定义一个int型的vector
	v.push_back(1);
	v.push_back(3);
	v.push_back(2);
	cout << "现在有的元素：";
	print(v);
	cout << endl;
	cout << "v.front()=" << v.front() << endl;;
	cout << "v.back()=" << v.back() << endl;
	cout << "v.size()=" << v.size() << endl;
	cout << endl;

//倒置、排序
	reverse(v.begin(), v.end());
	cout << "倒置后：";
	print(v);
	sort(v.begin(), v.end());
	cout << "正向排序后：";
	print(v);
	sort(v.rbegin(), v.rend());
	cout << "逆向排序后：";
	print(v);

//插入元素
	v.insert(v.begin() + 2, { 5,6 });
	cout << "插入5,6后：";
	print(v);
	cout << endl;

//插入元素
	v.erase(v.begin() + 1);//删除某处的元素
	cout << "删除第二个元素后：";
	print(v);
	cout << endl;
	v.pop_back();//删除最后一个元素
	cout << "删除最后一个元素后";
	print(v);
	cout << endl;

//判断是否为空
	cout << "v.empty() = " << v.empty()<<endl;//方法一
	cout << "v.size()=" << v.size() << endl;//方法二
	cout << endl;

//清空
	v.clear();
	cout << "清空后：";
	cout << "v.empty() =" << v.empty()<<endl;
	cout << "v.size()=" << v.size() << endl;
}
```
## 双指针
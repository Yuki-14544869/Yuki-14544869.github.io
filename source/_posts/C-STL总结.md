---
title: C++ STL总结
date: 2017-08-24 16:39:01
tags:
  - C++
  - ACM
---
# C++ STL总结

## String

### length && size

`size_t size() const noexcept;`**返回 string 长度。**
>string::length() 与 string::size() 完全相同。

### substr

`string substr (size_t pos = 0, size_t len = npos) const;`**产生子串**
返回一个新建的初始化为 string 对象的子串的拷贝 string 对象。  
子串是，在字符位置 pos 开始，跨越 len 个字符（或直到字符串的结尾，以先到者为准）对象的部分。

```C++
string str="We think in generalities, but we live in details.";
string str2 = str.substr (3,5);     // "think"
string str3 = str.substr (3);     // get from "think" to the end
```

### string()

`String(number, character)`**返回 string**

```C++
z=string(3,"w")   //"www"
z=string(3,"aw")  //"awa"
z=string(3,"www") //"www"

vector<char> v;
v.push_back('a');
v.push_back('b');
v.push_back('c');
z = string(v.begin(), v.end()); //"abc"
```

### empty

**true if the string length is 0, false otherwise.**

### insert

#### 返回插入的第一个字母的 iterator 以及修改过后的 str

```C++
// inserting into a string
#include <iostream>
#include <string>

int main ()
{
  std::string str="to be question";
  std::string str2="the ";
  std::string str3="or not to be";
  std::string::iterator it;

  // used in the same order as described above:
  str.insert(6,str2);                 // to be (the )question
  str.insert(6,str3,3,4);             // to be (not )the question
  str.insert(10,"that is cool",8);    // to be not (that is )the question
  str.insert(10,"to be ");            // to be not (to be )that is the question
  str.insert(15,1,':');               // to be not to be(:) that is the question
  it = str.insert(str.begin()+5,','); // to be(,) not to be: that is the question
  str.insert (str.end(),3,'.');       // to be, not to be: that is the question(...)
  str.insert (it+2,str3.begin(),str3.begin()+3); // (or )

  std::cout << str << '\n';
  return 0;
}
```
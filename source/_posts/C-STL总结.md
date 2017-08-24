---
title: C++ STL总结
date: 2017-08-24 16:39:01
tags:
  - C++
  - ACM
---

# String
## length && size
`size_t size() const noexcept;`**返回 string 长度。**
>string::length() 与 string::size() 完全相同。

## substr
`string substr (size_t pos = 0, size_t len = npos) const;`**产生子串**
返回一个新建的初始化为 string 对象的子串的拷贝 string 对象。 
子串是，在字符位置 pos 开始，跨越 len 个字符（或直到字符串的结尾，以先到者为准）对象的部分。
```
string str="We think in generalities, but we live in details.";
string str2 = str.substr (3,5);     // "think"
string str3 = str.substr (3);     // get from "think" to the end
```

## string()
`String(number, character)`**返回 string**
```
z=string(3,"w")   //"www"
z=string(3,"aw")  //"awa"
z=string(3,"www") //"www"

vector<char> v;
v.push_back('a');
v.push_back('b');
v.push_back('c');
z = string(v.begin(), v.end()); //"abc"
```

## empty
**true if the string length is 0, false otherwise.**
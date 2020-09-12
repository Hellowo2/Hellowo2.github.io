---
layout: post
title: 'c语言字符串模式匹配'
date: 2020-09-12
author: lalalla
cover: 'http://on2171g4d.bkt.clouddn.com/jekyll-banner.png'
tags: c语言 BruteForce
---
### 我是沙雕
## 我是沙雕
```c
int index(string *s,string *t,int pos)
{
    int i,j;
    if(pos<1 || pos>s->length || pos>s->length-t+1)
    return 0;
    i=pos-1;
    j=0;
    for(i<s->length && j<t->length)
    {
        if(s->ch[i]==t->ch[j])
        {
            i++;
            j++;
        }
        else
        {
            i=i-j+1;
            j=0;
        }
    }
    if(j>=t->length)
    {
        printf("匹配成功\n");
        system("pause");
        return i-t->length+1;
    }
    else
    {
        printf("匹配不成功\n");
        system("pause");
        return 0;
    }
}
```

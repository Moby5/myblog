Title: tfidf关键词抽取
Slug: gen-keywords
Date: 2017-05-16 20:00
Category: python
Tags: jieba keywords tfidf
author: jkmiao
Summary: a simple demo of how to extract keywords from chinese text.


针对一篇文档进行关键词抽取的场景经常会碰到，在此备记一个简单利用jieba库进行关键词抽取的方法，抛砖引玉。

## 安装

```
    pip install jieba --user_keywords.txt
```

## 使用

```python
    
    import jieba
    import re
    from jieba import analyse
    
    # 载入自定义词典
    jieba.load_userdict("data/user_keywords.txt")
    # 载入停用词
    analyse.set_stop_words("data/stop_words.txt")
    # tfidf获取关键词
    def get_keywords(text, topK=10):
        """
        :type text: str
        :type topK int: 默认抽取个数
        :rtype : str
        """
        key_words = analyse.extract_tags(text, topK=topK)
        # 过滤掉纯数字
        key_words = filter(lambda x: not re.search('\d+', x), key_words)
        return " ".join(key_words)

```

This is my 2nd post, and I'll try to write one every 2 days. The more the better.

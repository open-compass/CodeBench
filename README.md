# CodeBench

## 介绍
LCBench由爬取的Leetcode中英周赛题目组成，具体为第274次至第378次周赛的全部题目，包括其中穿插的双周赛。

## 数据格式
数据储存在 [LCBench-v0.1](https://github.com/open-compass/CodeBench/tree/main/LCBench-v0.1) 文件夹下。样例如下：

中文：
```json
{
    "Contest id": "378/2982", 
    "text_name": "找出出现至少三次的最长特殊子字符串 II", 
    "text": "给你一个仅由小写英文字母组成的字符串 s 。\n如果一个字符串仅由单一字符组成，那么它被称为 特殊 字符串。例如，字符串 \"abc\" 不是特殊字符串，而字符串 \"ddd\"、\"zz\" 和 \"f\" 是特殊字符串。\n返回在 s 中出现 至少三次 的 最长特殊子字符串 的长度，如果不存在出现至少三次的特殊子字符串，则返回 -1 。\n子字符串 是字符串中的一个连续 非空 字符序列。", 
    "canonical_solution": "from collections import defaultdict\ndef maximumLength(s):\n        special_substrings = defaultdict(int)\n        start = 0\n        while start < len(s):\n            curr = start\n            while curr < len(s) - 1 and s[curr] == s[curr + 1]:\n                curr += 1\n            window_size = curr + 1 - start\n            for length in range(1, window_size + 1):\n                special_substrings[(s[start], length)] += window_size + 1 - length  \n            start = curr + 1\n        res = -1\n        for k in special_substrings:\n            if special_substrings[k] >= 3:\n                res = max(res, k[1])   \n        return res", 
    "entry_point": "maximumLength", 
    "test_list": ["assert maximumLength(\"aaaa\") == 2", "assert maximumLength(\"abcdef\") == -1", "assert maximumLength(\"abcaba\") == 1"], 
    "Difficulty": "MEDIUM"
}
```
英文：
```json
{
    "Contest id": "378/2982", 
    "text_name": "Find Longest Special Substring That Occurs Thrice II", 
    "text": "You are given a string s that consists of lowercase English letters.\nA string is called special if it is made up of only a single character. For example, the string \"abc\" is not special, whereas the strings \"ddd\", \"zz\", and \"f\" are special.\nReturn the length of the longest special substring of s which occurs at least thrice, or -1 if no special substring occurs at least thrice.\nA substring is a contiguous non-empty sequence of characters within a string.", 
    "canonical_solution": "from collections import defaultdict\ndef maximumLength(s):\n        special_substrings = defaultdict(int)\n        start = 0\n        while start < len(s):\n            curr = start\n            while curr < len(s) - 1 and s[curr] == s[curr + 1]:\n                curr += 1\n            window_size = curr + 1 - start\n            for length in range(1, window_size + 1):\n                special_substrings[(s[start], length)] += window_size + 1 - length  \n            start = curr + 1\n        res = -1\n        for k in special_substrings:\n            if special_substrings[k] >= 3:\n                res = max(res, k[1])   \n        return res", 
    "entry_point": "maximumLength", 
    "test_list": ["assert maximumLength(\"aaaa\") == 2", "assert maximumLength(\"abcdef\") == -1", "assert maximumLength(\"abcaba\") == 1"], 
    "Difficulty": "MEDIUM"
}
```
其中参考答案`canonical_solution`为排序最高的题解，难度`Difficulty`为LeetCode官方所标记的难度。
---
date: 2005-12-13 13:11:21
type: post
title_en: impression-of-googlecodejam
title: 参加了Google Code Jam
wordpress_id: 192
tags:
- tech
---

![Google Code Jam](http://static.flickr.com/34/73064519_27ca7904d8_m.jpg)

昨天参加本年度最居挑战意义的比赛 - Google Code Jam

哈哈, 关于这个比赛可真的是众说纷纭, 各种说法大家可以Google一把去看看, 在此就不做链接了!

言归正传, 看了GCJ(Google Code Jam)的宣传以后, 俺也有些动心. 高额的奖金, Google的offer机会, 估计是个人心里都要小荡漾一下了! 于是, 俺早早的就注册报名了. 就等着12月12日的来临呢! 张BB竟然还开始了算法练习(可能是巧合吧^_^).

比赛前听张BB说初赛巨松无比, 甚至可以先得到题, 然后随便找时间做, 只要在截止时间前提交就可以了. 后来证明, 不是我听错了, 就是他说错了. 当我上去拿题的时候, 我发现系统已经开始计时了, ft...只好硬着头皮现做.

由于手边还在处理着其他的事情, 中间还接了两个电话, 所以时间是肯定不够用了. 光第一道简单的题就用去了我将近半小时, 我当时那个FT啊...同时心里还在咒骂着张BB...^_^

结果当然是没有做完第二题. 硬着头皮提交了一个空程序, 呵呵...还得了一点儿分. (提交的时候得到的分数应该是时间上的分数, 提交的越快, 分数越高)

晚上去质问张BB. 他说没跟我这么说过, 那就估计是我听错了...再ft一个...也怪自己没有好好研究比赛规则, 算了, 不管了. 他也挺惨的, 写的时候网络断了, 而且IDE还出了问题. 哎...我们都是命苦的人淫啊...

说说这两题.

第一题就不说, 巨简单. 傻傻的我第一眼看完竟然想用搜索算法, 简直是疯了! 后来冷静下来, 原来这么弱智, 呵呵...我的答案在后面, 不觉得我的代码恶心的人就看看吧:)

第二题应该是一个回溯的问题. 如果放到高中那会儿, 估计这题也就半小时就能搞定! 可惜我现在大学毕业都快2年了, 虽然有思路, 但是手已经没有那么熟了...哎...难道我真要变成中国的程序员了么? 不行, 不能这样!

如果有人有更好的算法, 一定要和我交流! 我不甘心啊!

偶还有一点点小小的感触.

1. 不知道是不是因为是初赛的缘故, 题目并不是很难. 对于我来说, 还是理解题意用了些时间. 我感觉如果题目是中文的, 而且让一个正在准备NOI的高中生来做的话, 会很easy. 当然, 也不排除google的用意是在找能hack这两题的人;)

2. 我们完全有机会作弊! 如果一开始注册了两个账号, 哈哈, 那我的分数一定很高了!(嘿嘿, 其实一开始自己也是准备作弊, 谁知...怪自己)

3. 算法这东西是基础. 但是平时的工作中基本用不到. 让我又开始质疑自己了! 这个问题还是比较深的, **我又要自省了**

附上这两道题和我第一题的答案吧!

**250分的题**

Problem Statement

You are given a string[] cityMap representing the layout of a city. The city consists of blocks. The first element of cityMap represents the first row of blocks, etc. A 'B' character indicates a location where there is a bus stop. There will be exactly one 'X' character, indicating your location. All other characters will be '.'. You are also given an int walkingDistance, which is the maximum distance you are willing to walk to a bus stop. The distance should be calculated as the number of blocks vertically plus the number of blocks horizontally. Return the number of bus stops that are within walking distance of your current location.

Definition

Class: BusStops  
Method: countStops  
Parameters: string[], int  
Returns: int  
Method signature: int countStops(string[] cityMap, int walkingDistance)  (be sure your method is public)

Constraints

- cityMap will contain between 1 and 50 elements, inclusive.
- Each element of cityMap will contain between 1 and 50 characters, inclusive.
- Each element of cityMap will contain the same number of characters.
- Each character of each element of cityMap will be 'B', 'X', or '.'.
- There will be exactly one 'X' character in cityMap.
- walkingDistance will be between 1 and 100, inclusive.

Examples

0)

	{"...B.",
	".....",
	"..X.B",
	".....",
	"B...."}
	3

Returns: 2

You can reach the bus stop at the top (3 units away), or on the right (2 units away). The one in the lower left is 4 units away, which is too far.

1)

	{"B.B..",
	".....",
	"B....",
	".....",
	"....X"}
	8

Returns: 3

A distance of 8 can get us anywhere on the map, so we can reach all 3 bus stops.

2)

	{"BBBBB",
	"BB.BB",
	"B.X.B",
	"BB.BB",
	"BBBBB"}
	1

Returns: 0

Plenty of bus stops, but unfortunately we cannot reach any of them.

3)

	{"B..B..",
	".B...B",
	"..B...",
	"..B.X.",
	"B.B.B.",
	".B.B.B"}
	3

Returns: 7

**偶的解答**

	using System;
	using System.Collections;
	
	namespace GCJ250
	{
		public class BusStops
		{
			public int countStops(string[] cityMap, int walkingDistance)
			{
				int result = 0;
	
				int height = cityMap.Length;
				int weight = cityMap[0].Length;
	
				// finding "X"&"b"
				int xx = -1;
				int xy = -1;
				ArrayList Bs = new ArrayList();
	
				for (int i = 0; i < height; i++)
				{
					for (int j = 0; j < weight; j++)
					{
						string _c = cityMap[i][j].ToString().ToLower();
						if (_c == "x")
						{
							xx = i;
							xy = j;
						}
						else if (_c == "b")
						{
							int [] _B = new int[2];
							_B[0] = i;
							_B[1] = j;
							Bs.Add(_B);
						}
					}
				}
	
				// calculating
				foreach (int [] b in Bs)
				{
					int bx = b[0];
					int by = b[1];
	
					if (Math.Abs(xx - bx) + Math.Abs(xy - by) <= walkingDistance)
						result ++;
				}
	
				return result;
			}
		}
	}

**750分的题**

Problem Statement

You are given a string[] grid representing a rectangular grid of letters. You are also given a string find, a word you are to find within the grid. The starting point may be anywhere in the grid. The path may move up, down, left, right, or diagonally from one letter to the next, and may use letters in the grid more than once, but you may not stay on the same cell twice in a row (see example 6 for clarification).

You are to return an int indicating the number of ways find can be found within the grid. If the result is more than 1,000,000,000, return -1.

Definition

Class: WordPath  
Method: countPaths  
Parameters: string[], string   
Returns: int  
Method signature: int countPaths(string[] grid, string find) (be sure your method is public)

Constraints

- grid will contain between 1 and 50 elements, inclusive.
- Each element of grid will contain between 1 and 50 uppercase ('A'-'Z') letters, inclusive.
- Each element of grid will contain the same number of characters.
- find will contain between 1 and 50 uppercase ('A'-'Z') letters, inclusive.

Examples

0)

	{"ABC",
	"FED",
	"GHI"}
	"ABCDEFGHI"

Returns: 1

There is only one way to trace this path. Each letter is used exactly once.

1)

	{"ABC",
	"FED",
	"GAI"}
	"ABCDEA"

Returns: 2

Once we get to the 'E', we can choose one of two directions for the final 'A'.

2)

	{"ABC",
	"DEF",
	"GHI"}
	"ABCD"

Returns: 0

We can trace a path for "ABC", but there's no way to complete a path to the letter 'D'.

3)

	{"AA",
	"AA"}
	"AAAA"

Returns: 108

We can start from any of the four locations. From each location, we can then move in any of the three possible directions for our second letter, and again for the third and fourth letter.

4 * 3 * 3 * 3 = 108.

4)

	{"ABABA",
	"BABAB",
	"ABABA",
	"BABAB",
	"ABABA"}
	"ABABABBA"

Returns: 56448

There are a lot of ways to trace this path.

5)

	{"AAAAA",
	"AAAAA",
	"AAAAA",
	"AAAAA",
	"AAAAA"}
	"AAAAAAAAAAA"

Returns: -1

There are well over 1,000,000,000 paths that can be traced.

6)

	{"AB",
	"CD"}
	"AA"

Returns: 0

Since we can't stay on the same cell, we can't trace the path at all.

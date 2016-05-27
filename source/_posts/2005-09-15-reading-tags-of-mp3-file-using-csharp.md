---
date: 2005-09-15 10:55:00
type: post
title_en: 2005-09-15-reading-tags-of-mp3-file-using-csharp
title: 用C#读取MP3文件的Tags
wordpress_id: 138
tags:
- tech
---

看到别人写的一个小东西，顺手用C#实现了。纯属娱乐。  

	using System;  
	using System.IO;  
	using System.Text;  
	
	namespace ShowMP3Tags  
	{  
		class Class1  
		{  
			[STAThread]  
			static void Main(string[] args)  
			{  
				if(args.Length == 0)  
				{  
					Console.WriteLine("Usage: ShowMP3Tags filename\n");  
					return;  
				}  
	
				if(!File.Exists(args[0].Trim()))  
				{  
					Console.WriteLine("File not found!\n");  
					return;  
				}  
	
				using(FileStream fs = File.OpenRead(args[0].Trim()))  
				{  
					ID3Tag tag = new ID3Tag();  
	
					fs.Seek(-128, SeekOrigin.End);  
					fs.Read(tag.TAGID, 0, tag.TAGID.Length);  
					fs.Read(tag.Title, 0, tag.Title.Length);  
					fs.Read(tag.Artist, 0, tag.Artist.Length);  
					fs.Read(tag.Album, 0, tag.Album.Length);  
					fs.Read(tag.Year, 0, tag.Year.Length);  
					fs.Read(tag.Comment, 0, tag.Comment.Length);  
					fs.Read(tag.Genre, 0, tag.Genre.Length);  
	
					Console.WriteLine(Encoding.Default.GetString(tag.Title));  
					Console.WriteLine(Encoding.Default.GetString(tag.Artist));  
					Console.WriteLine(Encoding.Default.GetString(tag.Album));  
					Console.WriteLine(Encoding.Default.GetString(tag.Year));  
					Console.WriteLine(Encoding.Default.GetString(tag.Comment));  
					Console.WriteLine(Encoding.Default.GetString(tag.Genre));  
	
					Console.ReadLine();  
				}  
			}  
		}  
	
		class ID3Tag  
		{  
			public byte [] TAGID = new byte[3]; // 3, 必须是TAG  
			public byte [] Title = new byte[30]; // 30, 歌曲的标题  
			public byte [] Artist = new byte[30]; // 30, 歌曲的艺术家  
			public byte [] Album = new byte[30]; // 30, 专辑名称  
			public byte [] Year = new byte[4]; // 4, 出版年代  
			public byte [] Comment = new byte[30]; // 30, 评论  
			public byte [] Genre = new byte[1]; // 1, 种类标识  
		}  
	}


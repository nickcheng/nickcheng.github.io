---
date: 2003-05-23 11:21:42
type: post
title_en: 2003-05-23-an-article-about-pointer-of-cpp-its-easy-to-know
title: 一篇C++讲指针的文章,很好懂! 
wordpress_id: 601
tags:
- tech
- beginner
- blogbus
- c++
- cpp
- pointer
---

标题 指针Guide chinahai（翻译）   
关键字 指针 C++   
出处 http://http://www.codeproject.com/  
译者序：  
  
　　这是一篇我所见过的关于指针的最好的入门级文章，它可使初学者在很短的  
时间内掌握复杂的指针操作。虽然，现在的JAVA、C＃等语言已经取消了指针，但  
作为一个C++程序员，指针的直接操作内存，在数据操作方面有着速度快，节约内  
存等优点，仍是很多C++程序员的最爱。指针就像是一把良剑，就看你怎么去应用  
它!  

　　有关这篇文章的技术性问题你可以写信给我：webmaster@chinahai.com.同时  
我的另外两篇相关文章《模板Guide》和《STL Guide》也快完成，希望能对您有  
所帮助！Loading... ...  
  
译者：万江(chinahai)  
  
什么是指针？  
  
　　其实指针就像是其它变量一样，所不同的是一般的变量包含的是实际的真实  
的数据，而指针是一个指示器，它告诉程序在内存的哪块区域可以找到数据。这  
是一个非常重要的概念，有很多程序和算法都是围绕指针而设计的，如链表。  
  
开始学习  
  
　　如何定义一个指针呢？就像你定义一个其它变量一样，只不过你要在指针名  
字前加上一个星号。我们来看一个例子：  

　　下面这个程序定义了两个指针，它们都是指向整型数据。  
  
	int* pNumberOne;  
	int* pNumberTwo;   
  
　　你注意到在两个变量名前的“p”前缀了吗？这是程序员通常在定义指针时的  
一个习惯，以提高便程序的阅读性，表示这是个指针。现在让我们来初始化这两  
个指针：   

	pNumberOne = &some_number;  
	pNumberTwo = &some_other_number;   

　　&号读作“什么的地址”，它表示返回的是变量在内存中的地址而不是变量本  
身的值。在这个例子中，pNumberOne 等于some_number的地址，所以现在  
pNumberOne指向some_number。 如果现在我们在程序中要用到some_number，我们  
就可以使用pNumberOne。  
  
我们来学习一个例子：  
  
　　在这个例子中你将学到很多，如果你对指针的概念一点都不了解，我建议你  
多看几遍这个例子，指针是个很复杂的东西，但你会很快掌握它的。  

　　这个例子用以增强你对上面所介绍内容的了解。它是用C编写的(注：原英文  
版是用C写的代码，译者重新用C++改写写了所有代码，并在DEV C++ 和VC++中编  
译通过！）  
  
	#include <iostream.h>  
	  
	void main()  
	{  
	// 声明变量：  
	int nNumber;  
	int *pPointer;  
	  
	  
	// 现在给它们赋值：  
	nNumber = 15;  
	pPointer = &nNumber;  
	  
	//打印出变量nNumber的值：  
	cout<<"nNumber is equal to :"<< nNumber<<endl;   
	  
	// 现在通过指针改变nNumber的值：  
	*pPointer = 25;  
	  
	//证明nNumber已经被上面的程序改变  
	//重新打印出nNumber的值:   
	cout<<"nNumber is equal to :"<<nNumber<<endl;   
	}  
  
　　通读一下这个程序，编译并运行它，务必明白它是怎样工作的。如果你完成  
了，准备好，开始下一小节。  
  
陷井！  
  
　　试一下，你能找出下面这段程序的错误吗？  
  
	#include <iostream.h>  
	  
	int *pPointer;  
	  
	void SomeFunction();  
	  
	{  
	int nNumber;  
	nNumber = 25;   
	  
	  
	//让指针指向nNumber:  
	pPointer = &nNumber;  
	}  
	  
	void main()  
	{  
	SomeFunction(); //为pPointer赋值  
	  
	//为什么这里失败了?为什么没有得到25  
	cout<<"Value of *pPointer: "<<*pPointer<<endl;  
	}  
  
　　这段程序先调用了SomeFunction函数，创建了个叫nNumber的变量，接着让指  
针pPointer指向了它。可是问题出在哪儿呢？当函数结束后，nNumber被删掉了，  
因为这一个局部变量。局部变量在定义它的函数执行完后都会被系统自动删掉。  
也就是说当SomeFunction 函数返回主函数main()时，这个变量已经被删掉，但  
pPointer还指着变量曾经用过的但现在已不属于这个程序的区域。如果你还不明  
白，你可以再读读这个程序，注意它的局部变量和全局变量，这些概念都非常重  
要。  

　　但这个问题怎么解决呢？答案是动态分配技术。注意这在C和C++中是不同  
的。由于大多数程序员都是用C++，所以我用到的是C++中常用的称谓。  
  
动态分配  
  
　　动态分配是指针的关键技术。它是用来在不必定义变量的情况下分配内存和  
让指针去指向它们。尽管这么说可能会让你迷惑，其实它真的很简单。下面的代  
码就是一个为一个整型数据分配内存的例子：   

	int *pNumber;  
	pNumber = new int;   

　　第一行声明一个指针pNumber。第二行为一个整型数据分配一个内存空间，并  
让pNumber指向这个新内存空间。下面是一个新例，这一次是用double双精型：   

	double *pDouble;  
	pDouble = new double;   

　　这种格式是一个规则，这样写你是不会错的。  

　　但动态分配又和前面的例子有什么不同呢？就是在函数返回或执行完毕时，  
你分配的这块内存区域是不会被删除的所以我们现在可以用动态分配重写上面的  

程序：   

	#include <iostream.h>  
	  
	int *pPointer;  
	  
	void SomeFunction()  
	{  
	// 让指针指向一个新的整型  
	pPointer = new int;  
	*pPointer = 25;  
	}  
	  
	void main()  
	{  
	SomeFunction(); // 为pPointer赋值  
	  
	cout<<"Value of *pPointer: "<<*pPointer<<endl;   
	}   

　　通读这个程序，编译并运行它，务必理解它是怎样工作的。当SomeFunction   
调用时，它分配了一个内存，并让pPointer指向它。这一次，当函数返回时，新  
的内存区域被保留下来，所以pPointer始终指着有用的信息，这是因为了动态分  
配。但是你再仔细读读上面这个程序，虽然它得到了正确结果，可仍有一个严重  
的错误。   
  
分配了内存，别忘了回收  
  
　　太复杂了，怎么会还有严重的错误！其实要改正并不难。问题是：你动态地  
分配了一个内存空间，可它绝不会被自动删除。也就是说，这块内存空间会一直  
存在，直到你告诉电脑你已经使用完了。可结果是，你并没有告诉电脑你已不再  
需要这块内存空间了，所以它会继续占据着内存空间造成浪费，甚至你的程序运  
行完毕，其它程序运行时它还存在。当这样的问题积累到一定程度，最终将导致  
系统崩溃。所以这是很重要的，在你用完它以后，请释放它的空间，如：   

	delete pPointer;   

　　这样就差不多了，你不得不小心。在这你终止了一个有效的指针（一个确实  
指向某个内存的指针）。  

　　下面的程序，它不会浪费任何的内存：  
  
	#include <iostream.h>  
	  
	int *pPointer;  
	  
	void SomeFunction()  
	{  
	// 让指针指向一个新的整型  
	pPointer = new int;  
	*pPointer = 25;  
	}  
	  
	void main()  
	{  
	SomeFunction(); //为pPointer赋值  
	cout<<"Value of *pPointer: "<<*pPointer<<endl;   
	  
	delete pPointer;  
	}　  
  
　　只有一行与前一个程序不同，但就是这最后一行十分地重要。如果你不删除  
它，你就会制造一起“内存漏洞”，而让内存逐渐地泄漏。  

　　(译者:假如在程序中调用了两次SomeFunction，你又该如何修改这个程序  
呢？请读者自己思考)  
  
传递指针到函数  
  
　　传递指针到函数是非常有用的，也很容易掌握。如果我们写一个程序，让一  
个数加上5,看一看这个程序完整吗？：   

	#include <iostream.h>  
	  
	void AddFive(int Number)  
	{  
	Number = Number + 5;  
	}  
	  
	void main()  
	{  
	int nMyNumber = 18;  
	  
	cout<<"My original number is "<<nMyNumber<<endl;   
	AddFive(nMyNumber);  
	cout<<"My new number is "<<nMyNumber<<endl;   
	//得到了结果23吗？问题出在哪儿？  
	}   

　　问题出在函数AddFive里用到的Number是变量nMyNumber的一个副本而传递给  
函数，而不是变量本身。因此， " Number = Number + 5" 这一行是把变量的副  
本加了5，而原始的变量在主函数main()里依然没变。试着运行这个程序，自己去  
体会一下。  

　　要解决这个问题，我们就要传递一个指针到函数，所以我们要修改一下函数  
让它能接受指针：把'void AddFive(int Number)' 改成 'void AddFive(int*   
Number)'　。下面就是改过的程序，注意函数调用时要用＆号，以表示传递的是  
指针：   

	#include <iostream.h>  
	void AddFive(int* Number)  
	{  
	*Number = *Number + 5;  
	}  
	  
	void main()  
	{  
	int nMyNumber = 18;  
	  
	cout<<"My original number is "<<nMyNumber<<endl;   
	AddFive(&nMyNumber);  
	cout<<"My new number is "<<nMyNumber<<endl;   
	}  
  
　　试着自己去运行它，注意在函数AddFive的参数Number前加*号的重要性：它  
告诉编译器，我们是把指针所指的变量加5。而不并指针自己加5。  
  
　　最后，如果想让函数返回指针的话，你可以这么写：   

	int * MyFunction();   

　　在这句里，MyFunction返回一个指向整型的指针。   
  
指向类的指针  
  
　　指针在类中的操作要格外小心，你可以用如下的办法定义一个类：   

	class MyClass  
	  
	{  
	　　public:  
	　　int m_Number;  
	　　char m_Character;  
	};   

　　接着你就可以定义一个MyClass 类的变量了：   

	MyClass thing;   

　　你应该已经知道怎样去定义一个指针了吧：   

	MyClass *thing;   

　　接着你可以分配个内存空间给它：   

	thing = new MyClass;   

　　注意，问题出现了。你打算怎样使用这个指针呢，通常你可能会  
写'thing.m_Number'，但是thing是类吗，不，它是一个指向类的指针，它本身并  
不包含一个叫m_Number的变量。所以我们必须用另一种方法：就是把'.'(点号）  
换成 -> ,来看下面的例子：   

	class MyClass  
	{  
	public:  
	int m_Number;  
	char m_Character;  
	};  
	  
	void main()  
	{  
	MyClass *pPointer;  
	pPointer = new MyClass;  
	  
	pPointer->m_Number = 10;  
	pPointer->m_Character = 's';  
	  
	delete pPointer;  
	}  
  
指向数组的指针  
  
　　你也可以让指针指向一个数组，按下面的方法操作：   

	int *pArray;  
	pArray = new int[6];   

　　程序会创建一个指针pArray，让它指向一个有六个元素的数组。另外一种方  
法，不用动态分配：   

	int *pArray;  
	int MyArray[6];  
	pArray = &MyArray[0];   

　　注意，&MyArray[0] 也可以简写成 MyArray ，都表示是数组的第一个元素地  
址。但如果写成pArray = &MyArray可能就会出问题，结果是 pArray 指向的是指  
向数组的指针（在一维数组中尽管与&MyArray[0]相等），而不是你想要的，在多  
维数组中很容易出错。  
  
在数组中使用指针  
  
　　一旦你定义了一个指向数组的指针，你该怎样使用它呢？让我们来看一个例  
子，一个指向整型数组的指针：  
  
	#include <iostream.h>  
	  
	void main()  
	{  
	int Array[3];  
	Array[0] = 10;  
	Array[1] = 20;  
	Array[2] = 30;  
	  
	int *pArray;  
	pArray = &Array[0];  
	  
	cout<<"pArray points to the value %d\n"<<*pArray<<endl;  
	}  
  
　　如果让指针指向数组元素中的下一个，可以用pArray++.也可以用你应该能想  
到的pArray + 1，都会让指针指向数组的下一个元素。要注意的是你在移动指针  
时，程序并不检查你是否已经移动地超出了你定义的数组，也就是说你很可能通  
过上面的简单指针加操作而访问到数组以外的数据，而结果就是，可能会使系统  
崩溃，所以请格外小心。  

　　当然有了pArray + 1，也可以有pArray － 1，这种操作在循环中很常用，特  
别是while循环中。  

　　另一个需要注意的是，如果你定义了一个指向整型数的指针：int*   
pNumberSet ，你可以把它当作是数组，如：pNumberSet[0] 和 *pNumberSet是相  
等的，pNumberSet[1]与*(pNumberSet + 1)也是相等的。  

　　在这一节的最后提一个警告：如果你用 new 动态地分配了一个数组，   

	int *pArray;  
	pArray = new int[6];   

　　别忘了回收，   

	delete[] pArray;   

　　这一句是告诉编译器是删除整个数组而不一个单独的元素。千万记住了。  
  
后话  
  
　　还有一点要小心，别删除一个根本就没分配内存的指针，典型的是如果没用  
new分配，就别用delete:  
  
	void main()  
	{  
	　　int number;  
	　　int *pNumber = number;  
	  
	　　delete pNumber; // 错误 - *pNumber 没有用new动态分配内存.  
	}  
  
常见问题解答  
  
Q：为什么我在编译程序时老是在 new 和 delete语句中出现'symbol   
undefined' 错误？  
A：new 和 delete都是C++在C上的扩展，这个错误是说编译器认为你现在的程序  
是C而不C++，当然会出错了。看看你的文件名是不是.cpp结尾。  
  
Q：new 和 malloc有什么不同？  
A：new 是C++中的关健字，用来分配内存的一个标准函数。如果没有必要，请不  
要在C++中使用malloc。因为malloc是C中的语法，它不是为面向对象的C++而设计  
的。  
  
Q：我可以同时使用free 和 delete吗？  
A：你应该注意的是，它们各自所匹配的操作不同。free只用在用malloc分配的内  
存操作中，而delete只用在用new分配的内存操作中。  
  
引用（写给某些有能力的读者）  
  
　　这一节的内容不是我的这篇文章的中心，只是供某些有能力的读者参考。  

　　有些读者经常问我关于引用和指针的问题，这里我简要地讨论一下。  

　　在前面指针的学习中，我们知道（＆）是读作“什么的地址”，但在下面的  
程序中，它是读作“什么的引用”  
  
	int& Number = myOtherNumber;  
	Number = 25;   

　　引用有点像是一个指向myOtherNumber的指针，不同的是它是自动删除的。所  
以他比指针在某些场合更有用。与上面等价的代码是：   

	int* pNumber = &myOtherNumber;  
	*pNumber = 25;   

　　指针与引用另一个不同是你不能修改你已经定义好的引用，也就是说你不能  
改变它在声明时所指的内容。举个例子：   

	int myFirstNumber = 25;  
	int mySecondNumber = 20;  
	int &myReference = myFirstNumber;  
	  
	myReference = mySecondNumber;//这一步能使myReference 改变吗？   
	  
	cout<<myFristNumber<<endl;//结果是20还是25？  
  
　　当在类中操作时，引用的值必须在构造函数中设定，例：  
  
	CMyClass::CMyClass(int &variable) : m_MyReferenceInCMyClass(variable)  
	{  
	　　// constructor code here  
	}   

总结   
  
　　这篇文章开始可能会较难掌握，所以最好是多读几遍。有些读者暂时还不能  
理解，在这儿我再做一个简要的总结：  

　　指针是一个指向内存区域的变量，定义时在变量名前加上星号（*）（如：  
int *number）。  

　　你可以得到任何一个变量的地址，只在变量名前加上＆（如：pNumber =   
&my_number）。  

　　你可以用'new' 关键字动态分配内存。指针的类型必须与它所指的变量类型  
一样（如：int *number 就不能指向 MyClass）。  

　　你可以传递一个指针到函数。必须用'delete'删除你动态分配的内存。  

　　你可以用&array[0]而让指针指向一个数组。  

　　你必须用delete[]而不是delete来删除动态分配的数组。  
  
　　文章到这儿就差不多结束了，但这些并不就是指针所有的东西，像指向指针  
的指针等我还没有介绍，因为这些东西对于一个初学指针的人来说还太复杂了，  
我不能让读者一开始就被太复杂的东西而吓走了。好了，到这儿吧，试着运行我  
上面写的小程序，也多自己写写程序，你肯定会进步不小的！  
  
from csdn

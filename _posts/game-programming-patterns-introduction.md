---
layout: patterns
title: 翻译－游戏编程模式－介绍
category: patterns
tags: [patterns]  
summery: 这是一本不错的关于游戏设计模式的书，一直很想翻译的，最近刚好有时间，准备开工！
image: /images/blog/game-programming-patterns.jpg
---

    作者英文网站[link](http://gameprogrammingpatterns.com/)
    本书目录[link](http://gameprogrammingpatterns.com/contents.html)
##介绍

    在小学五年级的时候, 我的朋友和我有了一点使用教室里几个破旧的TRS-80机器的权限。为了激励我们，一个老师找到了一份打印着一些BASIC程序的例子的打印资料让我们自己摆弄。
    电脑的音频磁带驱动器坏了，因此，每当我们想要执行代码时，我们都不得不仔细的从头开始输入。这使得我们更喜欢那些只有很少几行代码的程序：
       10 PRINT "BOBBY IS RADICAL!!!"
       20 GOTO 10
    即使如此，整个过程也充满失败的风险。我们不知道怎么编程，因此，一个微小的语法错误对我们来说也是无法逾越的难题。如果程序不能正常执行（这经常发生），我们不得不再从头开始。
    后面的一叠纸才是真正的变态“怪物”：一个程序的代码占用了几张纸，即使是尝试的念头也让我们纠结了好一会儿，但是，还说忍不住想要试试。程序上面的标题是：“洞穴与巨人”。我们根本不知道这个程序功能是什么，但是看起来像是一个游戏，还有什么比自己编写的电脑游戏更酷的事情呢？
    我们一直没有成功执行那个游戏，一年之后，我们搬出了那个教室（当我了解一些Basic之后，我意识到那个程序只是一个桌游的字符生成器，并不是一个游戏）。但是，对我的影响却很大，从那以后，我想成为一个游戏程序员。
    在我十几岁时，家里买了一台安装QuickBASIC的Macintosh，之后安装了THINK C。我把整个暑假都用在了游戏上面。自己学习是一个缓慢而痛苦的过程。开始我尝试执行一些简单东西，可能是一个地图菜单或者一个解谜。但是随着游戏的不断增大，游戏也变得越来越难。
    起初，要挑战的是让程序正常执行，之后，要想出怎么写比我想象中还要大的程序。在读了“How to Program in C++”，我开始尝试寻找其它关于如何组织程序的书籍。
    转眼几年过去了，一个朋友递给我一本书：设计模式:可复用面向对象软件的基础。终于找到了我从十几岁开始寻找的那本书，迫不及待的一口气从头看到尾。一直以来我都在挣扎如何编写优雅的代码，但是看到别人也在挣扎并有了解决方案，我如释重负。我感觉赤手空拳的我终于有了一些工具使用。
    在2001年，我找到自己梦想中的工作：成为EA的软件工程师。我迫不及待的想要看看专业人员是怎么把真实的游戏组装在一起的。像Madden Football这样大型游戏的架构是什么样的呢？不同系统间是怎么相互作用的呢？怎么只使用一套代码库让游戏支持多个平台呢？
    当打开源码时，一种震撼人心、惊奇的感觉油然而生。图形、AI、动画和视觉效果的代码都非常的卓越。这些人都知道如何从CPU中挤出每一个周期，并把这些周期用来做更好的事情。有些我之前都不知道可能的方法，他们已经开始使用了。
    但是，如何架构这些优秀代码被放在了事后。他们太专注于效果，而忽视了代码的组织架构。模块间的耦合度非常高。新的功能常常不论合适与否都放在了基础库。以我的眼光来说，这些程序员即使打开设计模式也只看了Singleton，之后的都没有看。
    当然，情况也不是那么坏。我想象的游戏程序员坐在满是白色书写板的象牙塔中，从容地连续几周讨论着架构细节。而现实世界我正看着的代码是那些为了赶在最后日期之前完成工作的人写的。他们尽了自己最大的努力，我逐渐意识到，最大努力经常是好的。我花越多的时间在游戏代码上，我就会发现更多隐藏在表面之下的光华。
    不幸的是，“隐藏”常常是一个好的形容。他们都是埋藏在代码中的精华，但是，很多人只从上面路过。我曾经看到同事努力的重新创造了一个好的解决方案，而他们需要的例子却安静地沉睡在他们之前的代码库中。
    这是本书希望解决的问题。我发掘并修改了我在游戏中发现的一些设计模式，并在这里展示给大家。这样我们可以把时间花在发明一些新的东西上面，而不用再重新发明这些模式。

## 市面上已有的书籍
    
    市面上已经有了很多关于游戏编程的书籍，为什么要再写一本？
    大部分游戏编程书记可以分为两类：
    1. 专业领域书籍。这些书局限于给你一个深入某些特定游戏开发方面的知识。他们将教你的是关于3D图形，实时渲染，物理仿真，人工智能或者音频。这些领域都是专业游戏开发者在职业生涯中必须的知识。
    2. 整个引擎方面的书籍。相比之下，这些书都是试图把各个不同部分组装成一个整体游戏引擎，他们面向于构建一个完整的某些特定类型游戏的引擎套件，通常是3D第一人称射击游戏。
    
    这两种类型的书籍我都很喜欢，但是，我想这中间还缺少了什么。特定领域的书仅仅告诉你那些代码是怎么与游戏其它模块交互的，你可能在物理和渲染方面是个奇才，但是，你知道怎么把他们优雅的组织在一起吗？
    第二类书只涵盖了这些，但是，我经常发现整个游戏引擎的书都太庞大和针对指定类型了。尤其是手机和休闲游戏的崛起，我们处在了一个有着许多不同题材类型游戏的时代，我们不能再只是仅仅复制Quake了。那些指导你的单一引擎在你的游戏不符合类型时变的没有太多用处了。
    取而代之的，我将要做的事更符合这样的需求，看菜单点菜。这本书的每一章都是独立的，你可以应用于你自己的代码中。这样你可以混合搭配出最符合你希望的游戏。
    
##与设计模式的相关性
    任何名字中带有“模式”的编程书籍，都明显和“设计模式:可复用面向对象软件的基础”有关（作者：Erich Gamma, Richard Helm, Ralph Johnson, and John Vlissides，被称为“Gang of Four”）。
    书名为“游戏编程模式”，并不是暗示“Gang of Four”的书不适用于游戏，相反，这本书在“Design Patterns Revisited”章节包含了许多设计模式中的模式。而本书的重点放在怎样将这些模式应用在游戏编程中。
    相反，我认为这本书同样适用于非游戏软件。我本可以叫这本书：更多设计模式，但是，我想游戏有更多有趣的例子。你真的想要读一本关于雇员记录和银行账户的书？
    话虽如此，本书中介绍的模式同样可以用于其它软件。我想这些模式对于在游戏开发中面临的通用挑战尤其适用，原因如下：
    1. 时间和序列经常是游戏架构的核心部分。事情必须发生在正确的次序和时间。
    2. 开发周期被高度压缩，程序员需要能迅速的在一组不同行为之上构建和迭代，而没有影响到彼此间的工作，对代码库也毫无影响。
    3. 所有行为都已经定义之后，开始交互。怪物攻击英雄，位置混合在一起，炸弹爆炸冲击敌人，相似的伙伴。那些交互应该在没有把基础代码变成混乱的毛球的情况下发生。
    4. 最后，性能对游戏来说很重要。游戏开发者都处于一个更古不变的竞赛中，看谁可以在他们的平台中“压榨”出更多的性能。节省循环周期技巧对不同游戏有不同意义。一个A级游戏，销售了百万份，帧率下降、愤怒的评审员。
    
## 怎么阅读本书
    游戏编程模式分为3个大的部分。第一部分为介绍和本书指引。即现在你正阅读的和接下来的一节。   
    第二部分,设计模式重游，重新解读一些“Gang of Four”中的模式。每一章，我都会讲解一下我自己对这个模式的理解，并说明本模式和游戏编程的关系。
    最后一部分是本书的干货。将展示我发现的十三个有用的设计模式，分为四类：序列模式、行为模式、解耦模式、优化模式。
    每个模式都使用统一的结构描述，这样你看把本书当作一本参考书，能快速找到你需要的：
    * 意图部分提供一个简要说明描述此模式打算要解决的问题。这是开始，因此你可以快速浏览本书发现可以帮助你解决当前问题的模式。
    * 动机部分描述了一个可以适用于具体问题例子的模式。不像具体的算法，一个模式通常没有具体的结构形式，除非用于解决某些特定的问题。没有例子的模式的教学就像教烘培不提及生面团一样纸上谈兵。这个部分提供“生面团”供下一部分用来“烘培”。
    * 模式部分提取之前例子的精髓部分。如果你想要一个对于此模式的精炼标准描述，这个就是。如果你之前已经熟悉此模式，想要确定自己没有忘记他的组成部分，那么此部分也是一个很好的温习。
    到此为止，要讲解的模式只是通过一个简单的例子解释。但是，你怎么知道这个模式是否能很好的解决你的问题呢？“使用时机”部分将提供一些“何时适合使用这个模式”和“何时应该避免使用这个模式”的指导。“铭记于心”部分指出使用这个模式时的后果和风险。
    如果你也和我一样需要具体的例子才能真正的理解使用，那么“例子代码”部分是你需要的。此部分通过一步一步执行让你知道此模式的工作原理。
    模式不同于单个的算法，因为，模式是开放式的。每次你使用一个模式，都有可能会有所改变。下一节，设计目标探索并展示不同的选择，决定何时使用一个模式。
    在结尾，有一个简短的“See Also”部分展示这个模式和其它模式的关系，并指向现实中使用这个模式的开源代码。
   
##关于示例代码
    本书例子代码均为C++，但是，并不表示这些模式不能用其它语言实现，或者C++比其它语言更好。几乎所有的语言都可以实现这些模式，尽管有些模式确实需要目标语言有对象和类为前提。
    为之所以选择C++的原因是，第一，C++是商业发行游戏方面最流行的语言，是这个工业领域的通用语言。尤其是，C++基于的C语言语法同样是JAVA、C#、JavaScript和其它一些语言的基础。即使你不了解C++，很大几率上也能通过一下努力明白示例代码。
    本书的目标不是教会你C++，示例也尽可能简单，并且不会使用完全的C++风格或者用法。阅读示例代码去理解其表达的意义，而不是代码本身。
    尤其是，代码并没有使用最新的C++ 11或者更新的风格。也没有使用标准库，更尽可能少用模板。对于C++代码来说这是“不好的”，但是，希望通过保持简约让C、Objective-C、Java和其它语言的人能更容易理解。
    为了避免浪费代码空间，那些你已经看过的或者与模式不相关的代码将会被省略。当出现这样的情况时，一个省略号将代替消失的代码出现在例子中。
    考虑到一个功能将会进行一些工作，并返回一个值。这样的模式将会以一个带有返回值的、工作没有完成来说明，示例代码将会是下面这样：
    bool update()
    {
      // Do work...
      return isDone();
    }
   
##何去何从
    模式在软件开发中经常不断改变、扩展，本书继续发扬始于Gang of Four揭示和分享的软件模式，这一过程将继续被后人传承下去。
    你也是这个过程的核心部分。因为，你开发出自己的模式，并改进本书中的模式（或者反驳本书中的模式）。你把这些贡献给软件社区。如果你有任何建议、补正、其它反馈，请联系我。
   
        

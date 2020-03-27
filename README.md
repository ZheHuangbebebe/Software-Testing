# Software Testing 笔记
竞争对手的程序死掉叫*崩溃*，自己的程序死掉叫*不良反应*（idiosyncrasy)。通常，崩溃之后会显示“ID02”这样的信息，“ID”是idiosyncrasy的缩写，后面的数字表示产品应测试的月份数。  
**软件失败的术语：**  
缺点（defect）偏差（variance）故障（fault）失败（failure）问题（problem）不一致（inconsistency）错误（error）事件（incident）缺陷（bug）异常（anomaly）  

只有**至少满足下列5个规则之一**才称发生了一个*软件缺陷*（software bug）：  
1. 软件未实现产品说明书要求的功能。
2. 软件出现了产品说明书指明不应该出现的错误。
3. 软件实现了产品说明书未提到的功能。
4. 软件未实现产品说明书虽未明确提及但应实现的目标。
5. 软件难以理解、不易使用、运行缓慢或者——从测试员角度看——最终用户会认为不好。

**软件缺陷出现的原因**
![](https://ucc.alicdn.com/pic/developer-ecology/43e42e78d7714658a39bc1b459428779.png )   

**测试文档**
* 测试计划(test plan): 描述用于验证软件是否符合产品说明书和苦湖需求的整体方案。包括质量目标、资源需求、进度表、任务分配、方法等。
* 测试用例(test case): 列举测试的项目，描述验证软件等详细步骤。
* 缺陷报告(bug report): 描述执行测试用例找出的问题。可以记录在纸上，但通常记录在数据库中。
* 测试工具和自动测试(test tool and automation): 之后将详细讨论
* 度量、统计和总结(metric, statistic, summary): 测试过程的总会。采用图形、表格和报告等形式。

*测试员*或*质量保证*（Quality Assurance，QA）员负责找出并报告软件产品的问题。他们与开发小组全部成员在开发过程中密切合作，进行测试并报告发现的问题。  

### 软件开发生面周期模式
四种最常用的模式：
* 大爆炸模式：多数情况下，大爆炸模式**几乎没什么测试**
* 边写边改模式：与大爆炸模式类似，**测试在边写边改模式中未特别强调**，但是在边写代码和修复缺陷过程中举足轻重。
* 瀑布模式：一旦进入某个步骤便无法回溯。因为测试仅在最后进行，所以一些根本性问题可能出现在早期，但是直到准备发布产品是才可能发现。
* 螺旋模式（最受软件测试员喜欢）：因为通过参与最初的设计阶段，可以尽早地影响到产品，可以把产品的来龙去脉弄得很清楚。软件测试员的测试一直都在进行，所以最后一步只是验证表面所有部分都没有问题。

### 测试的原则
![enter image description here](https://img-blog.csdnimg.cn/20190506142238292.png?#pic_center)
1. 完全测试是不可能的。
2. 软件测试是有风险的行为。
3. 测试无法显示潜伏的软件缺陷。
4. 找到的软件缺陷越多，就说明软件缺陷越多。
5. 反复使用相同的测试软件最后会使软件具有抵抗力
6. 并非所有软件缺陷都要修复
	* 没有足够时间
	* 不算真正的软件缺陷
	* 修复的风险太大
	* 不值得修复  
	* 产品说明书从没有最终版本
	* 软件测试员在产品小组中不受欢迎 (?)
作出错误决策的后果（如 [英特尔奔腾处理器缺陷](https://zh.wikipedia.org/wiki/%E5%A5%94%E8%85%BE%E6%B5%AE%E7%82%B9%E9%99%A4%E9%94%99%E8%AF%AF)）  
### 软件测试的术语和定义
**精确(precision)和准确(accuracy)** 

![enter image description here](http://starasp.uit.yorku.ca/psycho/chs/pics_chs/postscript_f1.gif)  

**确认**(verification)和**验证**(validation)   
确认是保证软件符合产品说明书的过程；验证是保证软件满足用户要求的过程。
**测试**(testing)和**质量保证**(QualityAssurance,QA)
软件测试员的目标是尽可能早地找出软件缺陷，并确保缺陷得以修复；软件质量保证人员的主要职责是创建和执行改进软件开发过程并防止软件缺陷发生的标准和方法。

### 开始测试
**黑盒测试**(black-box testing)和**白盒测试**(white-box testing)
在黑盒测试中，软件测试员只需知道软件要做什么——而无法看到盒子里的软件是如何运行的。有时又称功能性测试(functional testing)或行为测试(behavioral testing)。
在白盒测试(有时称为透明盒测试(clear-box testing))中，软件测试员可以访问程序员的代码，并通过检查代码的线索来协助测试——可以看到盒子里面。  

**静态测试**(static testing)和**动态测试**(dynamic testing)
静态是指测试不运行的部分——只是检查和审核；动态测试是指通常意义上的测试——使用和运行软件。

### 静态黑盒测试——测试产品说明书
产品说明书是书面文档，而不是可执行程序，因此是静态的。

### 动态黑盒测试
不深入代码细节测试软件的方法称为*动态黑盒测试*。它是*动态的*，因为程序在运行——软件测试员想用户一样使用它；同时，它是*黑盒*(black-box),因为测试不知道程序如何工作——戴上眼罩。测试员输入数据、接受输出、检验结果。动态黑盒测试常常被称为*行为测试*，因为测试的是软件在使用过程中的实际行为。  

#### 通过性测试和失效性测试
在通过性测试(test-to-pass)时，实际上是确认软件至少能做什么，而不会考验其能力。软件测试员并不需要想尽办法让软件崩溃，仅仅运用最简单、最直观的测试用例即可。
纯粹为了破坏软件而设计和执行的测试用例称为失效性测试(test-to-fail)或*错误强制测试*。往往在确信软件再普通情况下能正确运行之后，就可以采取各种手段搞垮软件来找出软件缺陷了。

#### 等价类划分
选择测试用例的方法是*等价类划分*(equivalence partitioning)，等价划分是指分步骤地把无限的测试用例缩减得很小，但过程同样有效。  

#### 数据测试
数据包括键盘输入、鼠标单击、磁盘文件、打印输出等。
* 边界条件(boundary condition)：如果软件能在其边界运行，那么正常情况下就应该不会有什么问题。
* 次边界条件(sub-boundary condition)/内部边界条件(internal boundary condition)：有些边界在软件内部，最终用户几乎看不到，但是软件测试员仍有必要进行检查。
* 默认、空白、空值、零值和无
* 非法、错误、不正确和垃圾数据

#### 状态测试
*软件状态*(software state)是指软件当前所处等条件或者模式。
* 测试软件的逻辑流程
	1. 建立状态转换图
	2. 减少要测试的状态及转换的数量
	3. 进行具体的测试：测试状态及其转换包括检查所有的*状态变量*(state variable)——与进入和退出状态相关的静态条件、信息、值、功能等。
* 失败状态测试
	1. 竞争条件和时序错乱：*多任务*(multitasking)是指操作系统设计用来同时执行多个独立的进程。这些进程可以是电子表哥或者电子邮件这样的独立程序，也可以是同一个程序中不同的部分。*竞争条件*(race condition)一词源自很容易想到的情形——多个进程向终点冲刺，不知道谁会先到达。
	2. 重复、压迫和重负：
		* *重复测试*(repetition testing)是不断执行童谣的操作。最简单的是不同的启动、关闭程序。还可以反复读写数据或者反复选择同一个操作。
		* 压迫测试(stress testing)是使软件在不够理想的条件下运行——内存小、磁盘小、CPU速度慢、调制调解器速率低等。观察软件对外部资源的要求和依赖程度。**压迫测试就是将支持降到最低限度，目的在于尽可能低限制软件的必要条件**。  
		* 重负测试(load testing)是尽量提供条件任其发挥，让软件处理尽可能大的数据文件。最大限度的发觉软件能力。**时间也是一种重负测试**。

### 静态白盒测试
静态白盒测试实在不执行软件的条件下有条理地仔细审查软件设计、体系结构和代码，从而找出软件缺陷的过程，有时称为结构化分析。  
进行静态白盒测试的首要原因是今早发现软件缺陷，以找出动态*黑盒测试难以发现或隔离的软件缺陷*。另一个好处是为黑盒测试员提供思路。他们可以不必了解代码细节，通过听审查评论就可以确定有问题或者容易产生软件缺陷的特定范围。  

### 正式审查(formal review)
即进行进行白盒测试的过程。有四个基本要素。
* 确定问题
* 遵守规则
* 准备
* 编写报告  

审查类型：同事审查，走查(walthrough) ，检验(inspection)

### 编码标准和规范
标准的三个重要原则：
1. 可靠性
2. 可读性/维护性
3. 移植性

标准有四个主要部分组成：
1. 标题
2. 标准
3. 解释说明
4. 示例

#### 通用代码审查清单
讲述静态白盒测试在正式审查中检验软件是应该查找的问题。
* 数据引用错误：指使用未经正确声明和初始化的变量、常量、数字、字符串或记录而导致的缺陷。
* 数据声明错误：不正确的声明或使用变量和常量
* 计算错误：就三无法得到预期结果
* 比较错误：小于、大于、等于、不等于、真假——比较和判断错误可能由于边界条件问题
* 子程序参数错误：软件子程序不正确地传递数据
* 输出/输入错误：包括文件读取、接受键盘或者鼠标输入以及向打印机或者屏幕等输出设备写入错误。
* 其他：ASCLII，移植性，兼容性...  

### 动态白盒测试
动态白盒测试是指利用查看代码功能和实现方式得到的信息来确定哪些需要测试、那些不要测试、如何展开测试。动态白盒测试的另一个常用名称是*结构化测试*(structural testing)。  
动态白盒测试包括以下四个部分：
* 直接测试底层函数、过程、子程序和库。在Microsoft Windows中这称为应用程序编程接口(API)。
* 以完整程序的方式从顶层测试软件，但是根据软件运行的了解调整测试用例。
* 从软件获得读取变量和状态信息等访问权，以便确定测试与预期结果是否相符，同时，强制软件以正常测试难以实现的方式运行
* 估算执行测试时“命中”的代码量和具体代码，然后调整测试，去掉多余的测试用例，补充遗漏的用例。  

#### 动态白盒测试和调试
![enter image description here](https://img-blog.csdnimg.cn/20190507161650240.png?)  
动态白盒测试的目标是寻找软件缺陷。*调试*(debugging)的目标是修复缺陷。


### 单元测试和集成测试
在底层进行的测试称为*单元测试*(unit testing)或者*模块测试*(module testing)。单元经过测试，底层软件缺陷被找出并修复后，就集成在一起，对模块组合进行*集成测试*(integration testing)。这个不断增加的测试过程继续进行，加入越来越多的软件片段，直至整个产品——至少是产品的主要部分——称为*系统测试*(system testing)的过程中一起测试。这种递增测试有两条途径：*自底向上*(bottom-up)和*自顶向下*(top-down)。

### 数据覆盖
把软件代码分成数据和状态(或程序流程)。从同样的角度看软件，可以相当容易地把得到的白盒信息映射到已经写完的黑盒测试用例上。首先考虑数据。数据包括所有变量、常量、数组、数据结构、键盘和鼠标输入、文件、屏幕输入/输出，以及调制解调器、网络等其他设备的输入和输出。

* 数据流(data flow)：主要是指在软件中完全跟踪一批数据。
* 次边界：如果进行白盒测试，就需要仔细检查代码，找到此边界条件，并建立能测试它们的测试用例。
* 公式和等式：公式和等式通常深藏于代码中，从外部看，其形式和影响并不是非常明显。
* 错误强制(error force)：如果执行在调试器中测试的程序，不仅能够观察到变量的值——还可以强制改变变量的值。

### 代码覆盖(code coverage)
代码覆盖测试是一种动态白盒测试，因为它要求通过完全访问代码以查看运行测试用例是经过了哪些部分。

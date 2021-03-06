#学习笔记
## 第8周-第19课 | 高级动态规划
### 1. 动态规划、状态转移方程串讲
> * 提纲
> * 1. 动态规划的复习；附带递归、分治。
> * 2. 多种情况的动态规划的状态转移方程串讲。
> * 3. 进阶版动态规划的习题。
> * 递归
> * 首先递归本身就是函数自己调用自己叫做递归。也就是递归和分治或者和回溯其实没有各个所谓的是A就不是B之间的关系，它其实就是定义一个问题的不同的方面，本身它的函数调用是自己调用自己就可以叫做是递归。最关键的是把递归的模板记住，一定一些递归就想到这个模板，然后可以背诵出来，下笔如有神。
> * 分治
> * 分治就是分而治之，仅此而已。它肯定要用递归，当然可以不写出递归的程序让它分而治之也是可以的，如果是强行起循环也是可以的。但是计算机本身设计的语言角度来说，绝大部分用递归写得话是非常自然的，就是做分治这里。所以还是要改变自己的思维习惯，就是切换成机器或者是程序语言的思维，也就是说递归经常要用。
> * 分治代码模板它本身代码的模板套用递归的代码部分，首先是中止条件，然后是所谓的准备数据和拆分问题，同时每一个子问题都调分治函数进行递归求解，最后得到一些中间的结果合并起来，合并完了之后返回。
> * 排序和快速排序和归并排序就是这么一个结构。归并排序为例，归并排序就是一个典型的分而治之，把一个数组劈成两半，左边部分先排好序，右边部分再排好序的情况下，然后把他们进行merge，merge的过程最后就可以让整个数组变得有序，这就是所谓归并排序的思想。它的代码和分治的代码模板是异曲同工的。
> * 感触：
> * 1. 人肉递归低效、很累。
> * 2. 找到最近最简方法，也就是找到重复性，这个重复性最好是最近的重复性，将其拆解成可重复解决的问题。最近重复性的理解特别是最近两个字，就想成是最大公约数就好了，如果拆的非常小的时候，这个时候会发现递归就是非常累，因为程序会写的非常繁琐，这个时候就要找那种最大公约数的关系。
> * 3. 数学归纳法思维。其实是比较反人类的，因为很多时候人的思维习惯，在现实中就是希望把每一个步骤自己都能够看到和把控，不然心里会没有底。一般很难会觉得只要把下一层管好，同时再指定整个制度，让下一层再把下一层管好，最后整个体系就是完美的。所以人一般不适合这种思想，但是要处理复杂的问题，或者在复杂的公司里面工作，或者在复杂的社会里面要工作，都是要用这样一种管理的方式，也就是同理可得的方式。自己要慢慢来习惯这样的一种思维习惯。
> * 本质：寻找重复性 -> 计算机指令集 
> * 为什么寻找重复性？就是任何一个复杂问题，最后在面试中一般来说不超过十行，最为复杂的问题也不超过二十行到三十行。那么把这么复杂的问题，要用计算机指令，在十行二十行的程序能够完成，说明它肯定是有重复性的，那么重复性最后就反映在代码指令集上面肯定就是for循环或者是while循环或者是递归调用。
> * 分治算法的递归树和它的整个分而治之的情况，那么动态规划由此引申，它和分治其实没有非常显著或者是本质上的区别。但是很多时候发现当一个分治的问题，本身它的子问题具有所谓的重叠或者是所谓的最优子结构的时候，这个时候就会发现很多时候就可以去重或者是淘汰次优解。那么在这种情况下，这种分治的办法，如果能在中间每一步淘汰次优解，就变成了所谓的动态规划。
> * 举一个具体的例子，Fibonacci问题如果要算fib(6)的时候，就会一步一步往下进行探，如果用最为朴素的分治，不考虑任何重复子问题，反复计算的话，最后算出来的它的状态树是有很多重复计算。当发现有重复的问题，加一个缓存进去，也就是说分治再加上记忆化的缓存，这个时候就可以认为就已经从分治过渡到所谓的动态规划了。
> * 回溯
> * 动态规划
> * 1. 将一个复杂的问题分解称为各个简单的子问题，它其实就是一种分治的思想。
> * 2. 它有一个最优子结构，所以动态规划就是分治再加上最优子结构。
> * 3. 很多时候它的状态本身可以进行顺推，也就是从下到上往上推，这个和Fibonacci数列是一样的，与其在开始从fib(6)上面像一个树形结构往下走，那还是不如从下标为0123一直用Fibonacci数列的递推公式往上递推，最后就变成就写几个循环，如果是三维的话就三层嵌套，二维就两层嵌套循环。所以动态规划很多时候可以理解为动态递推。
> * 初学者可以从分治的角度再加上记忆化搜索来开始切入动态规划题目，然后再转为递推的问题，这样会觉得思维习惯上比较顺畅。如果内功练得越来越多的时候，建议直接从递推开始，因为大部分的动态规划，最后肯定是递推的程序是最为简化的，也是符合动态规划整体思想的。
> * DP顺推模板，本身就是一个嵌套的循环，然后从之前的DP的状态，推倒最新的DP的状态，最后还有DP反应最后的最终结果。从这里可以看到一点，本身模板并不复杂，第一个复杂的地方就是DP状态的定义需要经验，同时需要把现实的问题定义成一个数组里面保存状态，这个数组可能是一维的二维的三维的都有可能。第二个复杂的地方就是这个状态转移方程要怎么写。很多时候很简化的情况就是Fibonacci数列直接把dp [i - 1] 加上 dp [i - 2]，就等于dp [i] 了，但是更多的情况下会求一个最小值，或者可以累加累减，或者是在里面有一层小的循环，从之前的K个状态里面找出它的最值，放在这个地方。
> * 关键点
> * 动态规划和递归或者分治它没有本质上的区别（关键看有无所谓的最优子结构），它们的共性就是都是找到重复性和找到重复子问题，然后化繁为简，庖丁解牛的把一个大问题分解成哥哥重复的子问题。它的差异性就是动态规划用来处理有所谓中间的重复性以及所谓的最优子结构。在中途可以淘汰次优解。
> * 常见的DP题目和状态方程（一定要多回忆之前做过的DP的问题）
> * 爬楼梯问题
> * 这个所谓是老生常谈中的老生常谈，那么爬楼梯问题，第一点本质上可以转换成Fibonacci问题，第二点就是爬楼梯问题和硬币置换的问题有异曲同工之处，爬楼梯问题是每次上一步上两步，相当于每次用面值1面值2的硬币，最后要凑成比如说面值为100的整体的硬币。递推公式：f(n) = f(n-1), f(1) = 1, f(0) = 0
> * 不同路径问题，递推公式：f(x,y) = f (x - 1, y) + f (x, y - 1)
> * 打家劫舍问题，DP的定义有两种方案。
> * 最小路径问题和以及在一棵树也就是一个三角形里面，从上到下找它的经过的路径最大的也非常常见，很经典的一个问题。
> * 股票买卖问题，这里有一个所谓的solution，就是一道题来团灭所有的股票买卖问题，这是一个非常好的题目，而且也是非常好的一个解决的解题报告。
> * 股票买卖问题有一个系列的题目，这里最关键的有几点，第一每天都有不同的股票价格，所以天很自然而然地称为一个状态定义的维度了。第二及时当前拥有股票还是没拥有股票，所以可以增加第二个维度，0和1表示拥有或者没有拥有。第三个有些题目会要求最多只能交易一次或者两次或者K次，所以在必须创建第三个维度，也就是说当前交易了多少次。这个次数可以是0123一直到大K，也就是最多不能超过K次。冷冻期这问题要怎么区别，所谓的冷冻期就是和偷房子问题是类似的，前一天买卖了这一天就不能买卖。
> * 它的状态模式可以是0或者1这样一个表示他拥有的股票和没有拥有的股票，他不管在哪个状态，当天他可以做的一个操作就是买或者是卖或者不做事。没有持仓就可以买，持仓的话就可以卖或者是不动。所以它的状态转移就是0通过买变成1，1通过卖变成回到0，当然它各自的状态都可以不动。
> * 这样一种把问题抽象化定义成状态，以及马上套用模板写出嵌套循环，把DP方程写下来，这样一个思维过程，一定要做得非常熟练。 第一步定义出状态树，第二步状态转移方程列出来。这两步一定要多练习，这就是整个动态规划的内功所在。
> * 作业：写出前面6道股票买卖问题。
> * 高阶的DP问题

## 第8周-第20课 | 字符串算法
### 1. 字符串基础知识和引申题目
> * 字符串最基本的一些操作，最重要的的就是在字符串里面如何运用算法和其它的数据结构来解决各种问题。
> * 字符串在面试的时候出的比较频繁，所以比较重要。同时会和递归以及动态规划相结合，所以一定要反复要对这个章节的题目进行练习，这些都是很重要的题目。
> * 字符串基础知识
> * 字符串是怎么定义的？注意的是Python和Java这个String它是immutable的不可变的，也就是说定义了这个String之后它就是不可变的，当把它加一个字母或者减一个字母它其实是新生成了一个String，原来的Sting还是原来的内容。那C++它是可变的，这一点一定要记清楚。所以不管用Python还是用Java，每次改变String里面的内容，其实都是创建了一个新的String，immutable的好处就是它是线程安全的，那么可变的话就可能在多线程的环境里面有一些问题。
> * Java、C#、JavaScript、Python、Go，String都是不可变的。Ruby和PHP，String是可变的。C最典型的C肯定是可变的，那个时候都没有字符串，它就是一个字符数组，最后用-0来结束的，C++后来就出来了String，但是它是mutable的，如果要让它变成不可变的，那就加const即可。Swift里面String也是可变的，但是可以用let来让它变成不可变的。
> * 关于可变与不可变的性质，有可能面试的时候面试官会问，所以一定要弄清楚。
> * 遍历字符串
> * 最常用的及时遍历String里面的每一个字符串，如何遍历呢？Python直接for in ，Java可以用i下标来做，然后调用string.charAt，最后就可以输出。也可以把它转换成CharArray之后，然后遍历里面所有的值，这样的话就可以把这个String里面的所有字符一一打出来。C++其实也同理可得，也可以用iterator。
> * 字符串比较
> * 在比较的时候要注意，主要是Java以及Python和JavaScript里面也有相应的问题，如果在Java里面x==y，它是比较它们的指针，比较它们的reference的地址，而不是比较字符串里的内容。那么x = "abb" 和 x = "abb" ，那么这两个是不同的变量，所以它指向内存中的不同地址。虽然它里面装的字符串的内容都是一样的，但是它们是不同的内存上的地址，所以x == y 就是false。在Java里面要怎么办？有两个函数系统给提供了一个是.equals，就来比较x是否和y里面的内容是否相同，同时还可以用.equalslgnoreCase忽略它的大小写。
> * 字符串处理的相关题目和由此引申出来的相关算法
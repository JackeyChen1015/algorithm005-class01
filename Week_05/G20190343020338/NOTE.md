#学习笔记
## 第5周-第12课 | 动态规划
### 1. 动态规划的实现以及关键点
> * 分治 + 回溯 + 递归 + 动态规划
> * 它们的本质其实就是将一个复杂的问题，分解成各种子问题，同时寻找它的重复性。
> * 不管说是分治、回溯、递归还是动态规划，它们并没有本质上的非常大的不一样，很多时候就是一些小的细节的问题。
> * 任何一个知识点和题目的话，最好都要做五遍。
> * 首先递归代码的模板，一定要死记硬背下来，就是形成机械式的记忆，一说这个马上就可以写出来了。
> * 递归模板里面主要是四步，把这四步记住就行了。
> * 递归中止条件：terminator
> * 处理当前层逻辑
> * 递归到下一层去：drill down
> * 有些时候需要的话就要恢复当前层状态，如果改变的状态都是在参数上面的话，因为递归调用的时候这个参数是会被复制的。如果是简单变量的话，那就不需要恢复这么一个过程。
> * 分治：它是递归的一种特殊形式。
> * 为什么是分治呢？就是因为世界上很多的大的复杂的问题，它其实都是有所谓的自相似性，也就是它的重复性。正是因为如此，那么计算机强就强在可以飞快地循环而飞快地运算。
> * 那么我们要做的事情就是把一个大的问题，把它分解成几个子问题。子问题一，子问题二，同时每个子问题也类似地分解成其他的相同的小的子问题，然后分别运算，运算出来之后再把结果返回，同时把结果聚合在一起。
> * 分治的模板拿起笔在纸上写一遍也可以拿电脑敲，但是在纸上写的话就直接写简码，然后把要点写出来，一般来说更便于人脑进行记忆。
> * 分治代码模板也是四步：
> * 首先还是是递归中止条件
> * 然后进行子问题拆分
> * 调子问题的递归函数，也就是drill down那一步，对每一个子问题调递归的函数进行类似的处理，处理完了之后就存在叫做subresult，这个可以随便取。
> * 最后就是将这些结果合并在一起。这就是所谓的分治，然后最后合并。
> * 最后有可能来自于递归就是当前层的状态需要进行恢复。
> * 感触
> 1. 人肉递归低效、很累。
> * 第一因为人脑的记忆很多时候其实并不准确，第二的话再计算的时候经常可能容易出错，同时递归多了，递归到第三层第四层，就不会记得上一层走成什么样子。所以人脑其实它的记忆准确性很差。
> 2. 找到最近最简方法，将其拆解成可重复解决的问题。
> * 用计算机来解决问题，最关键就是找到最近的最简的方法，将其分解成可重复解决的问题。
> * 假设这个题目就没有可重复的问题，这种情况的话可能就是它的复杂度本身就客观存在的，不能用循环或者递归来解决。那这样的话如果它的本身就是很复杂的话，一般来说它的代码量就会有比如说一两百行。
> * 这样的题目一般的话一般是不会出现在面试里，因为面试的题目的话一般就是十行二十行或者最多三四十行这样。
> * 如果参加面试的话，这个题目一开始看起来觉得很复杂的话，它肯定可以拆解为可重复解决的子问题。相当于一个面试的套路。当然在实践或者在公司里面写业务代码的话，如果它业务本身就是客观存在的复杂度，就很多很多的分支if else那就没办法，就只能硬写。
> * 3. 数学归纳法思维（抵制人肉递归的诱惑）
> * 解决类似于这种有重复子问题的问题的时候，要记得高中的时候学的数学归纳法，一定要养成数学归纳法的习惯。也就是说先把基础的条件，也就是当n = 1, n = 2的时候，它的最基本的条件是什么想明白，然后再解决当如果n成立的话，怎么推到n + 1。
> * 本质：寻找重复性 - > 计算机指令集
> * 为什么寻找重复性，就是计算机的指令集只会if else这种branch或者for循环，或者递归。所以的话因为它都是简单指令集，那么这个问题本身也就可以最后归结到循环来或者归结到递归来。那么要循环要递归就是有所谓的重复性。
> * 如果要进行人肉递归的时候为什么累？
> * 有些人说我对递归不熟，我的确想要先看下一下人肉递归怎么弄，那样也可以。这个时候就稍微勤奋一点或者别怕麻烦，就是把递归树给画出来。
> * 比如说我们要求Fibonacci数列第六个数的值，那就把这个递归树画出来。因为人脑其实记忆不那么准确，那用笔就行了。在纸上的话就把递归的状态树这么一个一个画出来。这时候会发现虽然只要计算第六个数，但是状态树可不是六个，它是2的N次方，所以你这个时间会发现它的结点的扩散是一个指数级的，也就是说它的状态是指数个，那么它的计算的复杂度，因为每个结点都要计算一次，所以它的计算的复杂度也是指数级的。
> * 通过这个过程会对一个问题它的状态树在脑子里面有一个树形结合的概念，这样的话对于初学者来说更方便理解。
> * 动态规划 Dynamic Programming，中文翻译的话非常玄乎叫做动态规划。
> * 那么其实它本质上要解决的问题就是一个递归问题或这是分治问题，但是它和普通的递归分治稍微有点不一样，就是第三点它拥有所谓的最优子结构。
> * Wiki的DP的定义里面programming其实和规划没有太大的关系，这里的programming指的是一种写程序的办法或者就是动态递推，programming很多时候在这里是进行推导的意思，所以可以理解为动态递推即可。
> * 最关键的这句话指的是将一个复杂的问题，把它分解成简单的子问题，定义里面还会加了一个括号，指的是用一种递归的方式。
> * Wiki的DP的定义里面明确说了，需要进行分治，也就是说DP本身的话和分治没有太大的不一样。那么它和分治很多时候本质的一个区别或者是明显的一个地方要注意的就是。一般来说动态规划的问题，它会是让你求一个最优解，或者求一个最大值，或者求一个最少的方式。这是因为它有所谓的这种最优子结构存在，那么在中间的每一步就不要把所以的状态都保存下来，只需要存最优的状态，当然还需要证明如果每一步都存着相当于最优的值，最后就能够推导出一个全局的最优的值。那么正式因为这样的话，就是引入了两个，一个的话就是有所谓的缓存了，或者是说状态的存储数组。第二个的话就是在每一步都会把次优的状态给淘汰掉，值保存在这一步里面最优或者较优的一些状态来推倒出最后的全局最优。
> * 关键点（一定要记载脑子里面）非常重要
> * 动态规划 Dynamuc Programming 或者叫 DP ，它的本质就是动态递推。
> * 动态规划 和 递归或者分治 没有根本上的区别 （关键是看有无最优的子结构）如果没有最优子结构说明所有的子问题都需要计算一遍，同时把最后的结构给合并在一起，所以传统意义上就称之为分治。非要叫动态规划行不行？其实也可以，就是因为可以理解为每次的最优解就是当前解就行了。它没有所谓的每次比较和淘汰的一个过程，但一般传统意义上称之为分治。
> * 共性：找到重复子问题
> * 差异性：动态一般认为就是有最优子结构，中途可以淘汰次优解，当然也必须淘汰次优解。如果把次优解都保存下来的话，那么会发现要做的事情的复杂度就会比淘汰次优解来的更多了。那么因为这个原因的话，所以动态规划很多时候是复杂度更低的，或者更加有效的。
> * 后面见的题目多了就会发现如果不进行淘汰的话，傻递归或者傻分治的话，经常是指数级的时间复杂度。但是如果进行了所谓的淘汰次优解那么经常会变成n的平方或者0(n)的时间复杂度，也就是从指数把复杂度降到了多项式级别。
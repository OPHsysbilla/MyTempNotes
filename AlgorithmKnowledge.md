本笔记只是备忘录，**并不是详细解决方案**，请使用`ctrl+F`查询

[TOC]
### Algorithm
#### 1. 打印字符串全排列  
递归后需要马上还原（因为所有的），因为递归是一颗深度优先的树（也就是栈），是先从叶子开始改变的
#### 2. 二叉搜索树转为双向链 
中序遍历二叉搜索树正好是递增的，只需要把结点左右指针连接中序中前后的结点。（二叉搜索树没有相同值的点）
#### 3. 递归求排列  
求排列时若用递归法，递归叶子回溯到父亲时需要还原改变（叶子最先改变，也就是说是从字符串数组最后两位开始的），不然就不是同一串字符串出发的（画出排列树推吧）
#### 3. 复制复杂链表 
每个结点复制一个接在该结点后面，a->a'->b->b'->c->c'，同时复制原结点所指向的任意结点，最后奇偶结点分离（跳着分离）
#### 4. 最小的k个数  
 partition函数（快排）最后得到的index就是他在序列中的位置，左边的就是前index个数。（期间可以用二分法逐渐缩小区间，由于是用一个固定位置的数作pivot所以最后得到的index是针对整个数组而言的）
#### 5. 集合和最大堆基于红黑树  
####  6. 最大子数组和 #### 
如果累加和为负则重新从新元素开始
####  7. 从1到n数里包含1的个数  
O(log10N) ， 十位上，每轮出现10次是指[10,19]这10个数	[解析](http://blog.csdn.net/yi_afly/article/details/52012593)  
####  8. 逆序对  
归并排序的同时进行计数
####  9. 数组排成最小的数  
可以用sprintf将数字写入字符串
####  10. 二叉树最低公共祖先  
（若是二叉搜索树）比一个结点大，比另一个结点小；（若有指向父节点的指针）寻找两个链表的公共结点；（什么都不是）用栈递归到叶子再逐个往上退栈。
####  11. 二叉树路径和等于某个数  
传递vector的引用（用vector作栈方便顺序输出），递归遍历，进入结点时压入该结点，退出时弹出（恢复成父节点进入的情景）
####  12. 不能继承的类  
虚拟继承virtual 父类，把父类构造函数设为私有，并且父类含有一个友元函数，友元函数的类型是由模板类给出的，所以虚拟继承的时候需要把子类的类型当成<typename>参数传入；（只能在堆上）私有构造与析构，用静态getInstance函数返回一个新的父类对象。
####  13. C++按类中声明的元素顺序初始化成员  
####  14.  求方程正整数解个数 
[求方程正整数解个数](https://www.nowcoder.com/questionTerminal/4a625528d7be46da8aaa4af999c40346)
#### 15. 多路平衡归并排序  
外排序，m个归并项（子表个数）k路归并的归并趟数s=logk(m)，[败者树](http://www.360doc.com/content/15/0719/22/22633806_486084820.shtml)
#### 16. n阶乘末尾0的个数  
（n除以5，即求5的质因数个数）
存在0必然是5*2的结果，所以必然含有5!(5*4*3*2*1)，所以只要求多少个5的倍数即可
#### 17. mongodb为什么没有自增id  
因为并发情况下同时插入,分布式存储的情况下无法协调分配连续数字（协调需要消耗网络资源），并且内部也不是按id顺序存的，因为文档长度可变，不知道什么时候文档变长要放到后面去
#### 18. 数n的约数个数  
（约数：能把别人整除的叫约数）自然数的约数的个数是有限的，质数的约数是1和本身；合数一定有3个以上的约数。由于约数个数定理知道：约数的个数等于:所有质因数的指数加上1后的乘积;
若一个数分解质因数后为(a^m)*(b^n),其中a,b均为质因数;m,n均为相应质因数的指数.
则约数个数为(m+1)(n+1).(因为a^0,a^1 ... a^m，都是它的约数共m+1个) 
> 例如:
(1)12=2^2 * 3,质因数有2和3,其指数分别为2和1,那么12的约数有(2+1) *(1+1)=6(个);
(2)60=22 * 3 * 5,质因数2, 3, 5的指数分别为2, 1, 1,那么60的约数有(2+1) * (1+1) * (1+1)=12(个)
#### 19. 一个数所有约数之和  
一个数所有约数之和 等于先把每个质因数从0次幂一直加到其最高次幂,再把每个相应质因数幂的和相乘.
若一个数分解为(a^m)*(b^n),则这个数所有约数的和为:
(a^0+a^1+a^2+a^3+…+a^m)(b^0+b^1+b^2+b^3+…+b^n).
>例如:
(1)12=22*3,则12所有约数的和为：(2^0+2^1+2^2)*(3^0+3^1)=7*4=28;
(2)60=22*3*5=(2^0+2^1+2^2)*(3^0+3^1)*(5^0+5^1)=7*4*6=168.
#### 20. Trie 树
#### 21. 需要同时移动多少步A和B才同时指向一个节点 ####
长度为100的循环链表，指针A和指针B都指向了链表中的同一个节点，A以步长为1向前移动，B以步长为3向前移动，一共需要同时移动多少步A和B才能再次指向同一个节点？

- 假定经过n步A、B再次相遇。则A经过的结点为n，B经过的结点为3n；此刻B必然比A多经过了整数倍的链表长度（圈的长度），假定经过了i倍的链表长度，则有3n-n=100i，即2n=100i；满足该等式的最小整数位i=2，n=100。即A经过了100个结点，B经过了300个结点，二者再次相遇。  
  - 也可以认为跑圈100m，A速度1m/s B速度3m/s，B比A多跑一圈耗时100/（3-1）=50s

#### 22. 模拟加减乘
注意 `  ^按位异或`   、`& 按位与`  、` | 按位或  `
##### 加法运算
将一个整数用二进制表示，其加法运算就是：相异（^）时，本位为1，进位为0；同为1时本位为0，进位为1；同为0时，本位进位均为0.
> 故不计进位的和为sum = a^b，进位就是arr = a&b,(与sum相加时先左移一位，因为这是进位）。完成加法直到进位为0.
```C++
int Add(int a, int b){
    return b ? Add(a^b, (a&b)<<1) : a;
}
```
##### 求相反数
```C++
//求a的相反数：将各位取反加一
int negative(int a){     //get -a
    return Add(~a, 1);
}

```
##### 减法运算
a-b  = a+(-b)　　
根据补码的特性，各位取反加1即可（注意得到的是相反数，不是该数的补码，因为符号位改变了）
（上面用二进制实现的加减法可以直接应用于负数）
```C++
int Minus(int a, int b)
{
    return Add(a, negative(b));
}
```
##### 乘法运算
原理上还是通过加法计算。将b个a相加
参考二进制数转十进制数，每位有一个2次幂的权重，当该位为1时，加上 2^x 倍 a
所以权重 a 不断 a<<=1
```C++
//正数乘法
int Multi(int a, int b){
    int ans = 0;
    while(b){
        if(b&1)
            ans = Add(ans, a);
        a = a << 1;
        b = b >> 1;
    }
    return ans;
}
//正数除法
int Divide(int a, int b)
{
    int coun = 0;
    while(a >= b)
    {
        a = Minus(a, b);
        coun = Add(coun, 1);
    }
    return coun;
}
```
##### 除法运算
除法运算是乘法的逆。看a最多能减去多少个b，

```C++
//判断是否是负数，0，正数
int isneg(int a)
{
    return a & 0x8000;
}
int iszero(int a)
{
    return !(a & 0xFFFF);
}
int ispos(int a)
{
    return (a&0xFFFF) && !(a&0x8000);
}

//处理负数的乘法和除法
int My_Multi(int a, int b)
{
    if(iszero(a) || iszero(b))
        return 0;
    if(isneg(a))
    {
        if(isneg(b))
            return Multi(negative(a), negative(b));
        else
            return negative(Multi(negative(a), b));
    }else if(isneg(b))
        return negative(Multi(a, negative(b)));
    else
        return Multi(a, b);
}

int My_Divide(int a, int b)
{
    if(iszero(b))
    {
        cout << "Error!" << endl;
        exit(1);
    }
    if(iszero(a))
        return 0;
    if(isneg(a))
    {
        if(isneg(b))
            return Divide(negative(a), negative(b));
        else
            return negative(Divide(negative(a), b));
    }else if(isneg(b))
        return negative(Divide(a, negative(b)));
    else
        return Divide(a, b);
}

```
>计算统中数值一律用补码来表示,因为补码可以使符号位和数值位统一处理，同时可以使减法按照加法来处理。
原码 -> 补码： 数值位取反加1 ` 数值位不包括符号位 `
补码 -> 原码： 对该补码的数值位继续 取反加1
补码的绝对值：（称为真值）正数的真值就是本身，负数的真值是各位（包括符号位）取反加1（即变成原码并把符号位取反） 
 b -> -b ： 各位（包括符号位）取反加1
#### 旋转字符：字符串前面的部分排在后面
"abcd"的旋转串是"abcd"，"bcda" ... "dabc"
首先目标串与原串长度要相等
- 可以设字符`s+s`，只要是`s+s`的子串都是旋转字符
比如：`"abcd"+"abcd"`，即`"abcdabcd"`中寻找子串，时间复杂度是根据查找子串的时间来定的，所以如果是采用KMP则是O(N)
#### 字符串提取出现的正负整数总和
注意可以` 负负得正 `
设置符号位positive，cur当前字符，num每一位不断往高位挪的积累数（字符串转化为数字），res数字总和
- 当cur为数字时，`num = num * 10 + positive? cur:-cur;`
- 当cur不为数字的时候，说明此时刚刚结束数字的转化，或者是开始部分没有数字，无论哪种都应该加上刚刚转化的数字num，并把num置零重新开始计数
` 此时需要注意当cur为负号时，前一位为负则positive=true，否则为负；如果不是负号，则重置positive为正 `
#### 字符串转换成int范围内数字
字符串可以是只出现一个0，即 ` 0 `
字符串不能出现 ` - `  、`  -0 ` 、`   -02 `  、`   A12 `
如果没有出现违法，只要检查是否每个字符都是数字就可以，
- 接下来进入判断，由于int范围是`-2147483648` 到 `2147483647`
先把所有的数字都转为负数（转为负数可以不用再写一遍正数的，最后如果是整数再负负得正回去）
- 判断是否溢出，因为`-214748364 * 10 + (-8)` 刚好是最大整数
先判断是否 `( res < = -214748364 )|| (res == -214748364 && cur <= -8 )`
同时也要注意如果是正整数，则转换后不能大于 2147483647
#### 字符串replace a with b
```C++
for(for...){
	if(a[i++]==b[j]){ 
		j++ ;
		if(j==源串长){ // 不用源串长-1，前面++过了
			标记a串 [i-源串长,i] 为0或者某个特定符表示需要删掉
			//（为了节省时间我们可以不删掉，只是不打印就可以）
		}
	}
	else j=0;
}
```
> 当a[i]=0而a[i-1]!=0时表示可以开始将前面积累的字符串打印了
` res = res + cur + to  `
> 注意最后是如果末尾全是0，没有到不是0的过度，我们需要再手动把这部分转换加上 `res += cur `
#### 计算连续出现字符的个数
aabbbcc -> a_2_b_3_c2
这种连续计数，在字符变化后结束上一轮计数的都是一种做法，注意末尾部分没有转换需要手动加上
- 本题从第二个字符开始判断每个字符和前一个字符如果不一样，进入转换，记录数字个数，重置计数个数为1（因为当转换出现，和前个不一样，前个计数为1，例如ab，从b开始，a计数为1）
> 如果是 a_2_b_3_c2 -> aabbbcc，求第5个字符是什么，此处是b
由于有"_"，可以因此分别数字与字符，保存当前字符cur，记录数字，当数字大于需要求的位置则返回
#### 判断是否每个字符只出现一次
可以用Map
但是如果只花费O(1)空间，只能使用堆排序，将数组排序对比前后是否相同

#### 浮点数高精度幂

#### 替换空为%20
先扫描一遍记录总长度为len+2*blank，再从后往前复制
> 一般挪动数组元素的，都需要从右往左复制

#### reverse字符串

##### reverse整个串
while(start<end){
	swap(c[start],c[end]);
	start++;
	end--;	
}

##### reverse前后部分顺序
abcde->deabc
先翻转abc，再翻转de，再翻转整个串

#### 变成回文串需要的最少字符
str长为N，$N*N$ 的动态规划表 dp[i][j]表示str[i..j]这段字符最少需要多个字符使str[i..j]变成回文串

dp[i][j]= \begin{cases} 0, & i=j   &
\\ 0 , &  str[i]=str[j] \quad and \quad |i-j|=2
\\ 1 , & str[i]!=str[j] \quad and \quad|i-j|\geq2  &
\\ dp[i+1]dp[j-1] , & str[i]=str[j] \quad and \quad |i-j|\geq2  &
\\ max{dp[i+1][j],dp[i][j-1]}+1 , & str[i]==str[j] \quad and \quad |i-j|\geq2&\end{cases}


未完待续

#### 判断最长左右括号
`()()` 与 `(())`合法，返回最长的合法出现的括号位置
- 先检查`(` 和 `)`的数量是否相等
- 设dp[i]表示str[0..i]位置上，以str[i]结尾的最长有效括号长度 $....(()())为6$
  1. str[i]==`(`，有效括号长度子串以`)`结尾，故dp[i]=0;
  2. str[i]==`)`，dp[i-1]代表str[i-1]结尾的最长有效括号长度，上一处没有被匹配过的位置`i-1-dp[i-1]`上如果是`(`，可以和str[i]凑成一对，此时dp[i]=dp[i-1]+2，同时dp[i-1]前面即str[i-2]之前的dp[i-2]也应该算上
- 最后求解 `Max(dp[0..N-1])` 就是最终结果

#### 计算字符串 4*((3*(-4)+-4*3))的结果
每次碰到`(`就进入递归进入下一层，`)`就结束递归，并传递参数 (char [], 下一个位置位置  )数组返回(计算的结果, 结束的位置)
....(char [] , int i){
	while(i < length && ch[i] !=')'){
		if( ch[i] 是数字 ){
			pre = pre * 10 + ch[i] - '0';
			i++;
		}else if (ch[i] 是操作符 ){
			队列a入队pre
			队列a入队ch[i]
			pre = 0;
			i++;
		}else(ch[i] == '('){
			array = 递归本函数(ch,i+1)
			pre = array[0];
			i = array[1]+1;
		}
	}
}
#### 整数N的二进制全排中0左边必有1的个数

#### 按顺序拼接字符串使总结果字典序最小
- 先按照拼接的方式将数组排列，即 return (a+b)>(b+a)
- 将排序后数组从头到尾组合起来
> 贪心算法，有详细需证明它的贪心策略是正确

#### 新类型字符a、Aa、AA 中第k个字符是哪种类型的
从k-1个字符开始往左对大写字母计数，碰到小写字母停止
- 根据奇偶判断`k`和`k+1`是AA，还是Aa，还是`k+1`是单独的a

#### 回文段最少切割数
dp[i]是子串str[i..len-1]需要切几次才能使str[i..len-1]全切成回文串，dp[0]是最后结果

从右往左，i初始为len-1
- 如果 str[i..j]是回文串,`dp[i]=dp[j+1]+1`，只需从str[j+1..len-1]寻找最经济的切割法
- j 从 [i..len-1] 遍历，`dp[i]=Min{dp[j+1]+1},i<=j<len且str[i..j]为回文串`
- 快速判断是否是回文串的方法是回文子串长度的相同方法，设`p[i][j]`为i..j间是否是回文串的判定
以下情况`p[i][j]`是回文串：
  - str[i..j]长度为1
  - str[i..j]长度为2，且2个字符相等
  - 子串str[i+1..j-1]是回文串（即p[i][j]=true），且str[i]==str[j]，最外面的两个字符串相等。
  - i 是从右往左，j是从i往右，所以`i..j`间长度是展开的便于计算p[i][j]
 
#### 全排列生成
除了next_permation以外，我们可以用如下框架的
```C++
//a[0...k]已经排好序，递归处理a[k..m]
void Perm(int a[],int k,int m){
	if(k==m) 打印a
	else       
		for(int i=k;i<m;i++){
			swap(a[k],a[i]);
			Perm(a,k+1,m);
			swap(a[k],a[i]);
		//还原调换的顺序
		}
}
```

#### 线性时间O(N)内寻找第k大
用随机Partition，平均可以到O(N)情况

####三个结点的二叉树个数
![三个结点的二叉树个数](http://uploadfiles.nowcoder.com/images/20150129/408620_1422498793365_2.png)

#### 活动安排（贪心）
- 所有活动先按结束时间排序
- 排序后如果上一个程序的结束时间大于（大于意味着在其时间点之后）下一个程序的开始时间，则两个活动冲突

#### 次最短路径

#### 含有寻找最小值Min功能的栈


#### Johnson图：用于稀疏图的，所有节点对的最短路径 

#### Time

 
#### 一排高楼里覆盖面积最大的矩阵
就像木桶效应一样，面积是由最矮的那栋楼决定的。高度*长度所以h[i]*(L-R)，如何搜索这个(L-R)呢？h[i]是L-R内最低的建筑的高度，所以h[L-1], h[L]..h[R], h[R+1]，其中h[L-1]及h[R+1]一定是小于L-R内最小高度的建筑的，不然h[L-1]就算入矩阵内了。
- 本题目标是找寻连续范围[L..R]，L-1是高度小于h[L]的下标小于L的最大下标（最靠近L），R-1同理是最靠近R的高度小于h[R-1]的最小下标
- 用栈。栈中保存的是比较后留下来的较小的高度，每到一个位置i，所有比h[i]高的高度都出栈，最后留下来的栈顶是符合要求的L（最近靠近i且高度小于h[i]，小于h[i]就不能保持h[i]的高度形成矩阵），为了保证是最靠近i的，所以每次经过i会将h[i]入栈，到i时肯定是靠近i的排在顶部。h[i]入栈前小于h[i]的已经出栈，所以栈内保存的是从栈顶开始越来越小的高度。
> 用三个数组h[i],L[i],R[i]计算$$h[i] = L[i]*R[i]$$


#### 求2个有序链表的公共部分
有序，所以若A链表的小，则A链表先行，若B链表小，B链表先行


#### 二叉树非递归先序、中序、后序遍历
##### 先序
```C++
void preOrderNoCur(Node* root){
    stack<Node*> s;
    s.push(root);
    while(!s.empty()){
        Node* head = s.top();//根
        s.pop();
        if(head->left){
            s.push(head->left);//左
        }else if(head->right){
            s.push(head->right);//右
        }
    }
}
```
##### 中序
```C++
/**/
void inOrderNoCur(Node* root){
    stack<Node*> s;
    Node* cur = root;
    while(!s.empty()||cur!=NULL){// 栈内还有结点 || 第一次访问  
        if(cur!=NULL){   // 试探cur结点是否还有左儿子
            s.push(cur);   //
            cur = cur->left;
        }else{    // 没有连续的左结点往下了
            Node* now = s.top();   // 出栈访问本身，再试探是否还有右儿子
            s.pop();
            print(now);
            cur = cur->right;     //  往右
        }        
    }
}
```
##### 后序
根结点入栈，保存最近一次刚刚访问的结点（为了判断左右孩子是否刚刚已经被访问过），每次取栈顶，如果栈顶的左右儿子为空或者都已经访问过，则访问栈顶并弹出
```C++
/**/
void inOrderNoCur(Node* root){
    stack<Node*> s;
    Node* cTop = NULL;// cTop当前栈顶
    Node* recentPrint = root;
    // recentPrint最近一次刚刚打印的结点
    s.push(root);
    while(!s.empty()){
        cTop = s.top();     
        //取栈顶，不弹出本结点
        if(cTop->left !=NULL &&  //当前结点的左结点存在
            cTop->left != recentPrint && 
            cTop->right != recentPrint  ){
            //  左结点不是刚刚打印过的结点，即还没访问过左结点（右结点是在左结点后面访问的）
            s.push(cTop->left);

        }else if(  cTop->right != NULL  &&  //当前结点的右结点存在
            cTop->right != recentPrint){
           //  右结点不是刚刚打印过的结点，即还没访问过
            s.push(cTop->right);
        }else{ //左右都访问过或者不存在
            print(cTop)  //出栈访问
            recentPrint = curTop;
            s.pop();
        }  
    }    
}
```

#### 链表排序
```C++
void sortLink(Node** head)
{
    if( head == NULL || head == NULL )
        return;
    
	Node* prev;
	Node* cur;
    // 从第三个开始排序
    cur = (*head)->next;
    (*head)->next = NULL;

    wihle(cur){
        prev = cur;
        cur = cur->next;
        if(prev->val < cur)


    }


}
```

#### 八数码
##### 逆序数
可计算这两个有序数列的逆序值，如果两者都是偶数或奇数，则可通过变换到达，否则，这两个状态不可达

#### 数据流中位数
两个堆，最大堆保存小数中的最大值，最小堆保存大数的最小值
当两个堆的个数和：
- 是偶数时，插入最小堆（是先要和最大堆里堆顶比较后选出的最大值）
- 是奇书时，插入最大堆（是先要和最小堆里堆顶比较后选出的最小值）

>> 其根本思想就是大小分开，各自占一半，最大堆存所有小数，小堆存所有大数，两堆堆顶是序列的中间两个数

#### 二叉树镜像
先交换父节点左右子树，再递归交换左右儿子结点的左右子树


#### 移位前是负数的，移位后仍是负数
移位时首位二进制位是不变的，为了保证移位前是负数的，移位后仍是负数


#### 超过一半的数：主元素

#### 旋转数组的最小数字
3,4,5,1,2，返回1
[low , mid , high]
如果是顺序增大的，即a[low]>a[high]直接返回a[low]；
如果mid属于前面，则增大low到mid；
如果mid属于后面，缩小high；
直到low，high相邻，且数字low>high
 **当三个指针所指的数相等时，只能顺序比较**

#### 寻找递减序列中的递增点（寻找逆序点）
[ 1,2,3,4,5,6 ]
[ 2,1,5,4,3,6 ] 中 1,5 和 3,6  和 6 ] 后逆序三次得到

#### 二叉树是否是镜像的
```
二叉树的镜像定义：源二叉树 
    	    8
    	   /  \
    	  6   10
    	 / \  / \
    	5  7 9 11
    	镜像二叉树
    	    8
    	   /  \
    	  10   6
    	 / \  / \
    	11 9 7  5
```
我们只需要比较**相同层是否是镜像**的就可以
同层有  [ 5 null null 5]  **注意用空当作占位符来比较是否是镜像的**
理所当然是**层次遍历**，即BFS的遍历方法
```C++
        queue<TreeNode*> curLayer;
        vector<TreeNode*> sonLayer;
        curLayer.push(cur);
        bool isSymmetric = true;
        while(!curLayer.size()){//还有儿子
            while(!curLayer.size()){
                TreeNode * front = curLayer.front();
                curLayer.pop(); 
                sonLayer.push_back(front->left); 
                sonLayer.push_back(front->right);  
            }
            vector<TreeNode*> son = &sonLayer;

            int len = sonLayer.size();
            for(int i =0;i<(len-1)/2;i++){
                if(son[i] != son[len-1-i]){
                    isSymmetric = false;
                    break;
                }
            }
            if(isSymmetric){
                for(int i =0;i< len ;i++){
                    if(sonLayer[i]){
                        curLayer.push(sonLayer[i]);
                    }
                }       
                sonLayer.clear();
            }
        }
        return isSymmetric;
```

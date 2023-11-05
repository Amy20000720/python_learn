---


---

<p>pandas的两大主要数据结构 Series和DateFrame</p>
<h1 id="一、series">一、Series</h1>
<h2 id="、定义">1、定义</h2>
<p>Series 是<strong>带标签</strong>的一维数组，可存储整数、浮点数、字符串、Python 对象等类型的数据。轴标签统称为**索引，<strong>它由两部分组成</strong>。</p>
<ul>
<li>values:一组数据(ndarray类型)</li>
<li>index:相关的数据索引标签<br>
<img src="https://pic4.zhimg.com/v2-6ff0e4a463f752a8ca6b421e2d244ffb_b.jpg" alt="enter image description here"></li>
</ul>
<h2 id="、创建">2、创建</h2>
<h3 id="列表创建">2.1 列表创建</h3>
<pre class=" language-python"><code class="prism  language-python"><span class="token keyword">import</span> pandas <span class="token keyword">as</span> pd
<span class="token comment"># Series组成部分：pd.Series(data=None, index=None, dtype=None, name=None, copy=False, fastpath=False)</span>
lst <span class="token operator">=</span> <span class="token punctuation">[</span><span class="token number">1</span><span class="token punctuation">,</span><span class="token number">3</span><span class="token punctuation">,</span><span class="token number">5</span><span class="token punctuation">,</span><span class="token number">6</span><span class="token punctuation">,</span><span class="token number">10</span><span class="token punctuation">,</span><span class="token number">23</span><span class="token punctuation">]</span>
s <span class="token operator">=</span> pd<span class="token punctuation">.</span>Series<span class="token punctuation">(</span>lst<span class="token punctuation">)</span> <span class="token comment"># 可以通过index指定索引，如果不指定索引，则会自动从0开始生成索引，我们叫做隐式索引</span>
s
</code></pre>
<p><img src="https://pic2.zhimg.com/v2-e792227d983ba0b45c6fb8e060467475_b.jpg" alt="enter image description here"></p>
<pre class=" language-python"><code class="prism  language-python">lst <span class="token operator">=</span> <span class="token punctuation">[</span><span class="token number">1</span><span class="token punctuation">,</span><span class="token number">3</span><span class="token punctuation">,</span><span class="token number">5</span><span class="token punctuation">,</span><span class="token number">6</span><span class="token punctuation">,</span><span class="token number">10</span><span class="token punctuation">,</span><span class="token number">23</span><span class="token punctuation">]</span>
s <span class="token operator">=</span> pd<span class="token punctuation">.</span>Series<span class="token punctuation">(</span>lst<span class="token punctuation">,</span>index<span class="token operator">=</span><span class="token punctuation">[</span><span class="token string">"A"</span><span class="token punctuation">,</span><span class="token string">"B"</span><span class="token punctuation">,</span><span class="token string">"C"</span><span class="token punctuation">,</span><span class="token string">"D"</span><span class="token punctuation">,</span><span class="token string">"E"</span><span class="token punctuation">,</span><span class="token string">"F"</span><span class="token punctuation">]</span><span class="token punctuation">)</span> <span class="token comment"># 通过index设置显式索引</span>
s
</code></pre>
<p><img src="https://pic3.zhimg.com/v2-276f89a6203dfe98d06b6ae6402f99ba_b.png" alt="enter image description here"></p>
<h3 id="numpy创建">2.2 numpy创建</h3>
<pre class=" language-python"><code class="prism  language-python">s <span class="token operator">=</span> pd<span class="token punctuation">.</span>Series<span class="token punctuation">(</span>np<span class="token punctuation">.</span>random<span class="token punctuation">.</span>randint<span class="token punctuation">(</span><span class="token number">1</span><span class="token punctuation">,</span><span class="token number">10</span><span class="token punctuation">,</span>size<span class="token operator">=</span><span class="token punctuation">(</span><span class="token number">3</span><span class="token punctuation">,</span><span class="token punctuation">)</span><span class="token punctuation">)</span><span class="token punctuation">,</span>index<span class="token operator">=</span><span class="token punctuation">[</span><span class="token string">'a'</span><span class="token punctuation">,</span><span class="token string">'b'</span><span class="token punctuation">,</span><span class="token string">'c'</span><span class="token punctuation">]</span><span class="token punctuation">)</span>
s
</code></pre>
<p><img src="https://pic3.zhimg.com/v2-bd95fa6f578c1e7f39fa04872a57512a_b.png" alt="enter image description here"></p>
<h3 id="字典创建">2.3 字典创建</h3>
<pre class=" language-python"><code class="prism  language-python">dic <span class="token operator">=</span> <span class="token punctuation">{</span><span class="token string">"A"</span><span class="token punctuation">:</span><span class="token number">1</span><span class="token punctuation">,</span><span class="token string">"B"</span><span class="token punctuation">:</span><span class="token number">2</span><span class="token punctuation">,</span><span class="token string">"C"</span><span class="token punctuation">:</span><span class="token number">3</span><span class="token punctuation">,</span><span class="token string">"D"</span><span class="token punctuation">:</span><span class="token number">2</span><span class="token punctuation">}</span>
s2 <span class="token operator">=</span> pd<span class="token punctuation">.</span>Series<span class="token punctuation">(</span>dic<span class="token punctuation">)</span>
s2
</code></pre>
<p><img src="https://pic2.zhimg.com/v2-bc7f3475ba1f037eb4a2adce56305bf5_b.png" alt="enter image description here"></p>
<h2 id="、series的索引和切片">3、series的索引和切片</h2>
<p>因为Series只有一列，因此一般只对行进行操作，索引分为隐式索引和显示索引，因此不同的方式操作起来也不一样。</p>
<h3 id="隐式索引">3.1 隐式索引</h3>
<pre class=" language-python"><code class="prism  language-python"><span class="token keyword">import</span> pandas <span class="token keyword">as</span> pd  
  
lst <span class="token operator">=</span> <span class="token punctuation">[</span><span class="token number">1</span><span class="token punctuation">,</span><span class="token number">3</span><span class="token punctuation">,</span><span class="token number">5</span><span class="token punctuation">,</span><span class="token number">6</span><span class="token punctuation">,</span><span class="token number">10</span><span class="token punctuation">,</span><span class="token number">23</span><span class="token punctuation">]</span>  
s <span class="token operator">=</span> pd<span class="token punctuation">.</span>Series<span class="token punctuation">(</span>lst<span class="token punctuation">)</span>  
<span class="token keyword">print</span><span class="token punctuation">(</span>f<span class="token string">'s:\n{s}'</span><span class="token punctuation">)</span>  
<span class="token keyword">print</span><span class="token punctuation">(</span>f<span class="token string">'s[0]取0行:\n{s[0]}'</span><span class="token punctuation">)</span>  
<span class="token keyword">print</span><span class="token punctuation">(</span>f<span class="token string">'s[[0,1]]取0行和1行:\n{s[[0,1]]}'</span><span class="token punctuation">)</span>  
<span class="token keyword">print</span><span class="token punctuation">(</span>f<span class="token string">'s[0:2]取0-2行，顾头不顾尾：0行和1行\n{s[0:2]}'</span><span class="token punctuation">)</span>  
<span class="token keyword">print</span><span class="token punctuation">(</span>f<span class="token string">'s.iloc[0:2]使用iloc来专门对隐式索引进行相关操作，也是只能取到0和1行，顾头不顾尾\n{s.iloc[0:2]}'</span><span class="token punctuation">)</span>  
<span class="token keyword">print</span><span class="token punctuation">(</span>f<span class="token string">'s.iloc[[0,1]]使用iloc来专门对隐式索引进行相关操作，跟s[[0,1]]一样\n{s.iloc[[0,1]]}'</span><span class="token punctuation">)</span>
</code></pre>
<pre class=" language-css"><code class="prism  language-css"><span class="token property">s</span><span class="token punctuation">:</span>
<span class="token number">0</span>     <span class="token number">1</span>
<span class="token number">1</span>     <span class="token number">3</span>
<span class="token number">2</span>     <span class="token number">5</span>
<span class="token number">3</span>     <span class="token number">6</span>
<span class="token number">4</span>    <span class="token number">10</span>
<span class="token number">5</span>    <span class="token number">23</span>
<span class="token property">dtype</span><span class="token punctuation">:</span> int<span class="token number">64</span>
s[<span class="token number">0</span>]<span class="token property">取0行</span><span class="token punctuation">:</span>
<span class="token number">1</span>
s[[<span class="token number">0</span>,<span class="token number">1</span>]]<span class="token property">取0行和1行</span><span class="token punctuation">:</span>
<span class="token number">0</span>    <span class="token number">1</span>
<span class="token number">1</span>    <span class="token number">3</span>
<span class="token property">dtype</span><span class="token punctuation">:</span> int<span class="token number">64</span>
s[<span class="token number">0</span><span class="token punctuation">:</span><span class="token number">2</span>]取<span class="token number">0</span>-<span class="token number">2</span>行，顾头不顾尾：<span class="token number">0</span>行和<span class="token number">1</span>行
<span class="token number">0</span>    <span class="token number">1</span>
<span class="token number">1</span>    <span class="token number">3</span>
<span class="token property">dtype</span><span class="token punctuation">:</span> int<span class="token number">64</span>
s<span class="token number">.</span>iloc[<span class="token number">0</span><span class="token punctuation">:</span><span class="token number">2</span>]使用iloc来专门对隐式索引进行相关操作，也是只能取到<span class="token number">0</span>和<span class="token number">1</span>行，顾头不顾尾
<span class="token number">0</span>    <span class="token number">1</span>
<span class="token number">1</span>    <span class="token number">3</span>
<span class="token property">dtype</span><span class="token punctuation">:</span> int<span class="token number">64</span>
s<span class="token number">.</span>iloc[[<span class="token number">0</span>,<span class="token number">1</span>]]使用iloc来专门对隐式索引进行相关操作，跟s[[<span class="token number">0</span>,<span class="token number">1</span>]]一样
<span class="token number">0</span>    <span class="token number">1</span>
<span class="token number">1</span>    <span class="token number">3</span>
<span class="token property">dtype</span><span class="token punctuation">:</span> int<span class="token number">64</span>

进程已结束,退出代码<span class="token number">0</span>
</code></pre>
<h3 id="显式索引">3.2 显式索引</h3>
<pre class=" language-python"><code class="prism  language-python">lst <span class="token operator">=</span> <span class="token punctuation">[</span><span class="token number">1</span><span class="token punctuation">,</span><span class="token number">3</span><span class="token punctuation">,</span><span class="token number">5</span><span class="token punctuation">,</span><span class="token number">6</span><span class="token punctuation">,</span><span class="token number">10</span><span class="token punctuation">,</span><span class="token number">23</span><span class="token punctuation">]</span>
s1 <span class="token operator">=</span> pd<span class="token punctuation">.</span>Series<span class="token punctuation">(</span>lst<span class="token punctuation">,</span>index<span class="token operator">=</span><span class="token punctuation">[</span><span class="token string">"A"</span><span class="token punctuation">,</span><span class="token string">"B"</span><span class="token punctuation">,</span><span class="token string">"C"</span><span class="token punctuation">,</span><span class="token string">"D"</span><span class="token punctuation">,</span><span class="token string">"E"</span><span class="token punctuation">,</span><span class="token string">"F"</span><span class="token punctuation">]</span><span class="token punctuation">)</span>
</code></pre>
<ul>
<li><strong>s1[“A”]</strong> 取某行或单个元素</li>
<li><strong>s1[[“A”,“B”]]</strong> 取多行，可以是连续的，也可以是不连续的</li>
<li><strong>s1[“A”:“B”]</strong> 切片，取A行和B行，这里的B行是可以取到的，头和尾都可以取到</li>
<li><strong>s1.loc[“A”:“B”]</strong> 使用loc来专门对显式索引进行相关操作，这里的B行也可以取到</li>
<li><strong>s1.loc[[“A”,“B”]]</strong> 使用loc来专门对显式索引进行相关操作</li>
</ul>
<h2 id="、基本操作">4、基本操作</h2>
<h3 id="显示部分数据">4.1 显示部分数据</h3>
<ul>
<li><strong>s.head(n)</strong> 该函数代表的意思是显示前多少行，可以指定显示的行数，不写n默认是前5行</li>
<li><strong>s.tail(n)</strong> 该函数代表的意思是显示后多少行，可以指定显示的行数，不写n默认是前5行</li>
</ul>
<h3 id="去重操作">4.2 去重操作</h3>
<p><img src="https://pic4.zhimg.com/v2-9c4da6afe7bd204db818656e067939f7_b.png" alt="enter image description here"></p>
<pre class=" language-python"><code class="prism  language-python">dic <span class="token operator">=</span> <span class="token punctuation">{</span><span class="token string">"A"</span><span class="token punctuation">:</span><span class="token number">1</span><span class="token punctuation">,</span><span class="token string">"B"</span><span class="token punctuation">:</span><span class="token number">2</span><span class="token punctuation">,</span><span class="token string">"C"</span><span class="token punctuation">:</span><span class="token number">3</span><span class="token punctuation">,</span><span class="token string">"D"</span><span class="token punctuation">:</span><span class="token number">2</span><span class="token punctuation">}</span>
s2 <span class="token operator">=</span> pd<span class="token punctuation">.</span>Series<span class="token punctuation">(</span>dic<span class="token punctuation">)</span>
s2<span class="token punctuation">.</span>unique<span class="token punctuation">(</span><span class="token punctuation">)</span>  <span class="token comment"># 原s2并未修改，该结果返回的是一维数组</span>
</code></pre>
<pre class=" language-css"><code class="prism  language-css"><span class="token function">array</span><span class="token punctuation">(</span>[<span class="token number">1</span>,<span class="token number">2</span>,<span class="token number">3</span>],dtype=int<span class="token number">64</span><span class="token punctuation">)</span>
</code></pre>
<h3 id="相加运算">4.3相加运算</h3>
<p><strong>Series相加，会根据索引进行操作，索引相同则数值相加，索引不同则返回NaN</strong></p>
<p>NaN在pandas解释中为 not a number ,它是float类型，表示缺失数据，可以参与运算。</p>
<pre class=" language-python"><code class="prism  language-python">```text
<span class="token comment"># s1</span>
lst <span class="token operator">=</span> <span class="token punctuation">[</span><span class="token number">1</span><span class="token punctuation">,</span><span class="token number">3</span><span class="token punctuation">,</span><span class="token number">5</span><span class="token punctuation">,</span><span class="token number">6</span><span class="token punctuation">,</span><span class="token number">10</span><span class="token punctuation">,</span><span class="token number">23</span><span class="token punctuation">]</span>
s1 <span class="token operator">=</span> pd<span class="token punctuation">.</span>Series<span class="token punctuation">(</span>lst<span class="token punctuation">,</span>index<span class="token operator">=</span><span class="token punctuation">[</span><span class="token string">"A"</span><span class="token punctuation">,</span><span class="token string">"B"</span><span class="token punctuation">,</span><span class="token string">"C"</span><span class="token punctuation">,</span><span class="token string">"D"</span><span class="token punctuation">,</span><span class="token string">"E"</span><span class="token punctuation">,</span><span class="token string">"F"</span><span class="token punctuation">]</span><span class="token punctuation">)</span>
<span class="token comment"># s2</span>
dic <span class="token operator">=</span> <span class="token punctuation">{</span><span class="token string">"A"</span><span class="token punctuation">:</span><span class="token number">1</span><span class="token punctuation">,</span><span class="token string">"B"</span><span class="token punctuation">:</span><span class="token number">2</span><span class="token punctuation">,</span><span class="token string">"C"</span><span class="token punctuation">:</span><span class="token number">3</span><span class="token punctuation">,</span><span class="token string">"D"</span><span class="token punctuation">:</span><span class="token number">2</span><span class="token punctuation">}</span>
s2 <span class="token operator">=</span> pd<span class="token punctuation">.</span>Series<span class="token punctuation">(</span>dic<span class="token punctuation">)</span>

s3 <span class="token operator">=</span> s2<span class="token operator">+</span>s1
</code></pre>
<p><img src="https://pic3.zhimg.com/v2-78d2a23d85a9b0401c2756994433ece2_b.png" alt="enter image description here"></p>
<h3 id="缺失值">4.4缺失值</h3>
<p><strong>查看Series中哪些是NaN</strong></p>
<p>二者都是判断是否为空，返回的结果为True或False</p>
<ul>
<li><strong>s.notnull()</strong> 不为空返回True，为空返回False</li>
<li><strong>s.isnull()</strong>  不为空返回False，为空返回True</li>
</ul>
<pre class=" language-text"><code class="prism  language-text">s3.isnull()
</code></pre>
<p><img src="https://pic4.zhimg.com/v2-e7316539b8f76d537c03a94aff5f7e7f_b.png" alt="enter image description here"></p>
<pre class=" language-text"><code class="prism  language-text">s3.notnull()
</code></pre>
<p><img src="https://pic3.zhimg.com/v2-8d35b95bd0ab74eb4fc8c395aa1a6d8e_b.png" alt="enter image description here"><br>
扩展</p>
<ul>
<li>
<p>需求1：只显示不为空的行</p>
<pre class=" language-text"><code class="prism  language-text">s3[s3.notnull()]
</code></pre>
</li>
<li>
<p>需求2：只显示为空的行</p>
<pre class=" language-text"><code class="prism  language-text">s3[s3.isnull()]
</code></pre>
</li>
</ul>
<p>链接：<a href="https://zhuanlan.zhihu.com/p/131553804">enter link description here</a></p>
<h1 id="二、dataframe">二、DataFrame</h1>
<h2 id="、定义-1">1、定义</h2>
<p>DataFrame就是由多个Series组成的，因此可以说DataFrame是Series的容器。<br>
DataFrame由3部分组成<br>
<strong>行索引:index</strong><br>
<strong>列索引:columns</strong><br>
<strong>值:values</strong><br>
<img src="https://pic1.zhimg.com/v2-926421856fd3d26ec8e98c3cec1b8ef4_b.jpg" alt="enter image description here"></p>
<h2 id="、创建-1">2、创建</h2>
<h3 id="numpy创建-1">2.1 numpy创建</h3>
<pre class=" language-python"><code class="prism  language-python"><span class="token comment">#  DataFrame的参数组成 pd.DataFrame(data=None, index=None, columns=None, dtype=None, copy=False)</span>
<span class="token comment"># index指定行索引，columns指定列索引，若不写，则默认从0开始，size指定行数和列数</span>
df <span class="token operator">=</span> pd<span class="token punctuation">.</span>DataFrame<span class="token punctuation">(</span>data<span class="token operator">=</span>np<span class="token punctuation">.</span>random<span class="token punctuation">.</span>randint<span class="token punctuation">(</span><span class="token number">1</span><span class="token punctuation">,</span><span class="token number">10</span><span class="token punctuation">,</span>size<span class="token operator">=</span><span class="token punctuation">(</span><span class="token number">2</span><span class="token punctuation">,</span><span class="token number">4</span><span class="token punctuation">)</span><span class="token punctuation">)</span><span class="token punctuation">,</span>index<span class="token operator">=</span><span class="token punctuation">[</span><span class="token string">"a"</span><span class="token punctuation">,</span><span class="token string">"b"</span><span class="token punctuation">]</span><span class="token punctuation">,</span>columns<span class="token operator">=</span><span class="token punctuation">[</span><span class="token string">"A"</span><span class="token punctuation">,</span><span class="token string">"B"</span><span class="token punctuation">,</span><span class="token string">"C"</span><span class="token punctuation">,</span><span class="token string">"D"</span><span class="token punctuation">]</span><span class="token punctuation">)</span>

</code></pre>
<p><img src="https://pic3.zhimg.com/v2-fd9c39dd9db12d770dc7fd0624519482_b.png" alt="enter image description here"></p>
<h3 id="字典创建-1">2.2 字典创建</h3>
<pre class=" language-python"><code class="prism  language-python">dic <span class="token operator">=</span> <span class="token punctuation">{</span><span class="token string">"name"</span><span class="token punctuation">:</span><span class="token punctuation">[</span><span class="token string">"张三"</span><span class="token punctuation">,</span><span class="token string">"李四"</span><span class="token punctuation">,</span><span class="token string">"王五"</span><span class="token punctuation">]</span><span class="token punctuation">,</span><span class="token string">"age"</span><span class="token punctuation">:</span><span class="token punctuation">[</span><span class="token number">1</span><span class="token punctuation">,</span><span class="token number">2</span><span class="token punctuation">,</span><span class="token number">3</span><span class="token punctuation">]</span><span class="token punctuation">}</span>
<span class="token comment"># key为列的索引，行索引则默认从0开始</span>
pd<span class="token punctuation">.</span>DataFrame<span class="token punctuation">(</span>dic<span class="token punctuation">)</span>
</code></pre>
<p><img src="https://pic3.zhimg.com/v2-2e7c098183778d2ec16e8eb62079c6b6_b.jpg" alt="enter image description here"></p>
<h2 id="、索引和切片">3、索引和切片</h2>
<h3 id="隐式索引-1">3.1 隐式索引</h3>
<pre class=" language-python"><code class="prism  language-python">df <span class="token operator">=</span> pd<span class="token punctuation">.</span>DataFrame<span class="token punctuation">(</span>data<span class="token operator">=</span>np<span class="token punctuation">.</span>random<span class="token punctuation">.</span>randint<span class="token punctuation">(</span><span class="token number">1</span><span class="token punctuation">,</span><span class="token number">10</span><span class="token punctuation">,</span>size<span class="token operator">=</span><span class="token punctuation">(</span><span class="token number">3</span><span class="token punctuation">,</span><span class="token number">4</span><span class="token punctuation">)</span><span class="token punctuation">)</span><span class="token punctuation">)</span>
</code></pre>
<p><img src="https://pic3.zhimg.com/v2-16f736be9514824004eacbf95e2ddd06_b.png" alt=""></p>
<ul>
<li><strong>df[0][0]</strong>  df[列][行]，获取隐式索引单个元素</li>
<li><strong>df[0:2]</strong> 对行的切片操作，获取的是0和1行，顾头不顾尾</li>
<li><strong>df[[0,1]] 对列的操作，获取第一列和第二列，跟Series不同</strong></li>
<li><strong>df.iloc[0:2,0:2] iloc对于隐式索引的操作，获取前两行和前两列组成的区域，逗号前式行，逗号后是列</strong></li>
<li><strong>df.iloc[[0,1],[0,1]] iloc对于隐式索引的操作，获取前两行和前两列组成的区域</strong></li>
</ul>
<h3 id="显式索引的操作">3.2 显式索引的操作</h3>
<pre class=" language-python"><code class="prism  language-python">df1 <span class="token operator">=</span> pd<span class="token punctuation">.</span>DataFrame<span class="token punctuation">(</span>data<span class="token operator">=</span>np<span class="token punctuation">.</span>random<span class="token punctuation">.</span>randint<span class="token punctuation">(</span><span class="token number">1</span><span class="token punctuation">,</span><span class="token number">10</span><span class="token punctuation">,</span>size<span class="token operator">=</span><span class="token punctuation">(</span><span class="token number">3</span><span class="token punctuation">,</span><span class="token number">4</span><span class="token punctuation">)</span><span class="token punctuation">)</span><span class="token punctuation">,</span>index<span class="token operator">=</span><span class="token punctuation">[</span><span class="token string">"a"</span><span class="token punctuation">,</span><span class="token string">"b"</span><span class="token punctuation">,</span><span class="token string">"c"</span><span class="token punctuation">]</span><span class="token punctuation">,</span>columns<span class="token operator">=</span><span class="token punctuation">[</span><span class="token string">"A"</span><span class="token punctuation">,</span><span class="token string">"B"</span><span class="token punctuation">,</span><span class="token string">"C"</span><span class="token punctuation">,</span><span class="token string">"D"</span><span class="token punctuation">]</span><span class="token punctuation">)</span>
</code></pre>
<p><img src="https://pic3.zhimg.com/v2-02d9c8a0baae3768e08138136c9d7c1a_b.png" alt=""></p>
<ul>
<li>**df[“A”] 或 df.A 获取单列，**类似于字典的操作</li>
<li><strong>df[‘A’][‘a’]</strong>  获取单个元素，先列后行 df[列][行]</li>
<li><strong>df[“a”:“b”]</strong>  获取是a到b行,包含b行</li>
<li><strong>df[[“A”,“B”]]</strong> 获取A列和B列</li>
<li>**df.loc[“a”:“b”,“A”:“B”] loc对于显式索引的操作，**df[行区域，列区域]</li>
<li><strong>df.loc[[“a”,“b”],[“A”,“B”]]</strong>  loc对于显式索引的操作，结果同上</li>
</ul>
<h2 id="、属性">4、属性</h2>
<h2 id="dataframe-的属性">4 DataFrame 的属性</h2>
<ul>
<li>df.values 值</li>
<li>df.columns 列</li>
<li>df.index 行</li>
<li>df.shape 几行几列（行，列）</li>
<li>df.size 大小，行数X列数<br>
<img src="https://pic2.zhimg.com/v2-906e01fa5ae42a5d99ebcf82d8a3fe09_b.jpg" alt="enter image description here"></li>
</ul>


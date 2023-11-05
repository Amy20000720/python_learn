---


---

<ul>
<li class="task-list-item"><input type="checkbox" class="task-list-item-checkbox" disabled=""> 2023年11月3日第一次修改</li>
</ul>
<h1 id="二、创建numpy">二、创建numpy</h1>
<pre class=" language-python"><code class="prism  language-python"><span class="token keyword">import</span> numpy <span class="token keyword">as</span> np  
arr <span class="token operator">=</span> np<span class="token punctuation">.</span>array<span class="token punctuation">(</span><span class="token punctuation">[</span><span class="token number">1</span><span class="token punctuation">,</span> <span class="token number">2</span><span class="token punctuation">,</span> <span class="token number">3</span><span class="token punctuation">]</span><span class="token punctuation">)</span> <span class="token comment"># 一维  </span>
<span class="token keyword">print</span><span class="token punctuation">(</span>arr<span class="token punctuation">,</span> <span class="token builtin">type</span><span class="token punctuation">(</span>arr<span class="token punctuation">)</span><span class="token punctuation">,</span> arr<span class="token punctuation">.</span>shape<span class="token punctuation">)</span>  
arr_1 <span class="token operator">=</span> np<span class="token punctuation">.</span>array<span class="token punctuation">(</span><span class="token punctuation">[</span><span class="token punctuation">[</span><span class="token number">1</span><span class="token punctuation">,</span> <span class="token number">2</span><span class="token punctuation">,</span> <span class="token number">3</span><span class="token punctuation">]</span><span class="token punctuation">,</span> <span class="token punctuation">[</span><span class="token number">4</span><span class="token punctuation">,</span> <span class="token number">5</span><span class="token punctuation">,</span> <span class="token number">6</span><span class="token punctuation">]</span><span class="token punctuation">]</span><span class="token punctuation">)</span> <span class="token comment"># 二维  </span>
<span class="token keyword">print</span><span class="token punctuation">(</span>arr_1<span class="token punctuation">,</span> <span class="token builtin">type</span><span class="token punctuation">(</span>arr_1<span class="token punctuation">)</span><span class="token punctuation">,</span> arr_1<span class="token punctuation">.</span>shape<span class="token punctuation">)</span>
</code></pre>
<h1 id="三、numpy数组的属性">三、numpy数组的属性</h1>

<table>
<thead>
<tr>
<th>属性</th>
<th>解释</th>
</tr>
</thead>
<tbody>
<tr>
<td>T</td>
<td>数组的转置（对高维数组而言）</td>
</tr>
<tr>
<td>dtype</td>
<td>数组元素的数据类型</td>
</tr>
<tr>
<td>size</td>
<td>数组元素的个数</td>
</tr>
<tr>
<td>ndim</td>
<td>数组的维数</td>
</tr>
<tr>
<td>shape</td>
<td>数组的维度大小（以元组形式）</td>
</tr>
<tr>
<td>astype</td>
<td>类型转换</td>
</tr>
</tbody>
</table><pre class=" language-python"><code class="prism  language-python"><span class="token comment"># 1、T：数组的转置（对高维数组而言）  </span>
a <span class="token operator">=</span> np<span class="token punctuation">.</span>array<span class="token punctuation">(</span><span class="token punctuation">[</span><span class="token punctuation">[</span><span class="token number">1</span><span class="token punctuation">,</span><span class="token number">2</span><span class="token punctuation">,</span><span class="token number">3</span><span class="token punctuation">]</span><span class="token punctuation">,</span><span class="token punctuation">[</span><span class="token number">4</span><span class="token punctuation">,</span><span class="token number">5</span><span class="token punctuation">,</span><span class="token number">6</span><span class="token punctuation">]</span><span class="token punctuation">]</span><span class="token punctuation">)</span>  
b <span class="token operator">=</span> a<span class="token punctuation">.</span>T  
<span class="token keyword">print</span><span class="token punctuation">(</span>a<span class="token punctuation">,</span><span class="token string">'\n'</span><span class="token punctuation">,</span>a<span class="token punctuation">.</span>shape<span class="token punctuation">,</span><span class="token string">'\n'</span><span class="token punctuation">,</span>b<span class="token punctuation">,</span><span class="token string">'\n'</span><span class="token punctuation">,</span>b<span class="token punctuation">.</span>shape<span class="token punctuation">)</span>  
<span class="token comment"># 2、dtype：数组元素的数据类型  </span>
c <span class="token operator">=</span> np<span class="token punctuation">.</span>array<span class="token punctuation">(</span><span class="token punctuation">[</span><span class="token punctuation">[</span><span class="token number">1</span><span class="token punctuation">,</span><span class="token number">2</span><span class="token punctuation">,</span><span class="token number">3</span><span class="token punctuation">]</span><span class="token punctuation">,</span><span class="token punctuation">[</span><span class="token number">4</span><span class="token punctuation">,</span><span class="token number">5</span><span class="token punctuation">,</span><span class="token number">6</span><span class="token punctuation">]</span><span class="token punctuation">]</span><span class="token punctuation">,</span>dtype <span class="token operator">=</span> np<span class="token punctuation">.</span>float32<span class="token punctuation">)</span>  
<span class="token keyword">print</span><span class="token punctuation">(</span>c<span class="token punctuation">,</span><span class="token string">'\n'</span><span class="token punctuation">,</span>c<span class="token punctuation">.</span>shape<span class="token punctuation">)</span>  
<span class="token comment"># 3、size：数组元素个数  </span>
<span class="token keyword">print</span><span class="token punctuation">(</span>f<span class="token string">'数组c的元素个数之和为：{c.size}'</span><span class="token punctuation">)</span>  
<span class="token comment"># 4、ndim：数组的维数  </span>
<span class="token keyword">print</span><span class="token punctuation">(</span>f<span class="token string">'数组c的维数：{c.ndim}'</span><span class="token punctuation">)</span>  
<span class="token comment"># 5、shape：数组的维度大小（以元组形式）  </span>
<span class="token keyword">print</span><span class="token punctuation">(</span>f<span class="token string">'数组c的形状：{c.shape}'</span><span class="token punctuation">)</span>  
<span class="token comment"># 6、astype：类型转换  </span>
d <span class="token operator">=</span> np<span class="token punctuation">.</span>array<span class="token punctuation">(</span><span class="token punctuation">[</span><span class="token number">1</span><span class="token punctuation">,</span><span class="token number">2</span><span class="token punctuation">,</span><span class="token number">3</span><span class="token punctuation">]</span><span class="token punctuation">,</span> dtype <span class="token operator">=</span> np<span class="token punctuation">.</span>float32<span class="token punctuation">)</span>  
e <span class="token operator">=</span> d<span class="token punctuation">.</span>astype<span class="token punctuation">(</span>np<span class="token punctuation">.</span><span class="token builtin">int</span><span class="token punctuation">)</span>  
<span class="token keyword">print</span><span class="token punctuation">(</span>f<span class="token string">'d的类型是：{d.dtype}，e的类型是：{e.dtype}'</span><span class="token punctuation">)</span>
</code></pre>
<h1 id="四、获取numpy数组的行列数">四、获取numpy数组的行列数</h1>
<p><mark>对于numpy我们一般多讨论二维的数组</mark></p>
<pre class=" language-python"><code class="prism  language-python">f <span class="token operator">=</span> np<span class="token punctuation">.</span>array<span class="token punctuation">(</span><span class="token punctuation">[</span><span class="token punctuation">[</span><span class="token number">1</span><span class="token punctuation">,</span><span class="token number">2</span><span class="token punctuation">,</span><span class="token number">3</span><span class="token punctuation">]</span><span class="token punctuation">,</span><span class="token punctuation">[</span><span class="token number">4</span><span class="token punctuation">,</span><span class="token number">5</span><span class="token punctuation">,</span><span class="token number">6</span><span class="token punctuation">]</span><span class="token punctuation">]</span><span class="token punctuation">)</span>  
<span class="token comment"># 获取numpy数组的行  </span>
<span class="token keyword">print</span><span class="token punctuation">(</span>f<span class="token string">'数组f的行数：{f.shape[0]}'</span><span class="token punctuation">)</span>  
<span class="token comment"># 获取numpy数组的列  </span>
<span class="token keyword">print</span><span class="token punctuation">(</span>f<span class="token string">'数组f的列数：{f.shape[1]}'</span><span class="token punctuation">)</span>
</code></pre>
<h1 id="五、切割numpy数组">五、切割numpy数组</h1>
<p>切分numpy数组类似于列表的切割，但是与列表的切割不同的是，numpy数组的切割涉及到行和列的切割，但是两者切割的方式都是从<mark>索引0</mark>开始，并且取头不取尾。</p>
<pre class=" language-python"><code class="prism  language-python">arr <span class="token operator">=</span> np<span class="token punctuation">.</span>array<span class="token punctuation">(</span><span class="token punctuation">[</span><span class="token punctuation">[</span><span class="token number">1</span><span class="token punctuation">,</span> <span class="token number">2</span><span class="token punctuation">,</span> <span class="token number">3</span><span class="token punctuation">,</span> <span class="token number">4</span><span class="token punctuation">]</span><span class="token punctuation">,</span> <span class="token punctuation">[</span><span class="token number">5</span><span class="token punctuation">,</span> <span class="token number">6</span><span class="token punctuation">,</span> <span class="token number">7</span><span class="token punctuation">,</span> <span class="token number">8</span><span class="token punctuation">]</span><span class="token punctuation">,</span> <span class="token punctuation">[</span><span class="token number">9</span><span class="token punctuation">,</span> <span class="token number">10</span><span class="token punctuation">,</span> <span class="token number">11</span><span class="token punctuation">,</span> <span class="token number">12</span><span class="token punctuation">]</span><span class="token punctuation">]</span><span class="token punctuation">)</span>  
<span class="token comment"># 取所有元素  </span>
<span class="token keyword">print</span><span class="token punctuation">(</span>f<span class="token string">'arr数组的全部元素：{arr[:,:]}'</span><span class="token punctuation">)</span>  
<span class="token comment"># 取第一行的所有元素  </span>
<span class="token keyword">print</span><span class="token punctuation">(</span>f<span class="token string">'arr数组第一行：{arr[0,:]}'</span><span class="token punctuation">)</span>  
<span class="token keyword">print</span><span class="token punctuation">(</span>f<span class="token string">'arr数组第一行：{arr[:1,:]}'</span><span class="token punctuation">)</span>  
<span class="token keyword">print</span><span class="token punctuation">(</span>f<span class="token string">'arr数组第一行：{arr[0,[0,1,2,3]]}'</span><span class="token punctuation">)</span>  
<span class="token comment"># 取大于5的元素，返回一个数组  </span>
<span class="token keyword">print</span><span class="token punctuation">(</span>arr<span class="token punctuation">[</span>arr <span class="token operator">&gt;</span> <span class="token number">5</span><span class="token punctuation">]</span><span class="token punctuation">)</span>  
<span class="token comment"># numpy数组按运算符取元素的原理，即通过arr &gt; 5生成一个布尔numpy数组  </span>
<span class="token keyword">print</span><span class="token punctuation">(</span>arr <span class="token operator">&gt;</span> <span class="token number">5</span><span class="token punctuation">)</span>
</code></pre>
<h1 id="六、numpy数组元素替换">六、numpy数组元素替换</h1>
<p><mark>.copy()</mark></p>
<pre class=" language-python"><code class="prism  language-python">arr_a <span class="token operator">=</span> arr<span class="token punctuation">.</span>copy<span class="token punctuation">(</span><span class="token punctuation">)</span>  
arr_a<span class="token punctuation">[</span><span class="token punctuation">:</span><span class="token number">1</span><span class="token punctuation">,</span><span class="token punctuation">:</span><span class="token punctuation">]</span><span class="token operator">=</span><span class="token number">0</span>  
<span class="token keyword">print</span><span class="token punctuation">(</span>f<span class="token string">'arr_a第一行的所有元素都是0：{arr_a}'</span><span class="token punctuation">)</span>
</code></pre>
<h1 id="七、numpy数组合并">七、numpy数组合并</h1>
<pre class=" language-python"><code class="prism  language-python">arr1 <span class="token operator">=</span> np<span class="token punctuation">.</span>array<span class="token punctuation">(</span><span class="token punctuation">[</span><span class="token punctuation">[</span><span class="token number">1</span><span class="token punctuation">,</span> <span class="token number">2</span><span class="token punctuation">]</span><span class="token punctuation">,</span> <span class="token punctuation">[</span><span class="token number">3</span><span class="token punctuation">,</span> <span class="token number">4</span><span class="token punctuation">]</span><span class="token punctuation">,</span> <span class="token punctuation">[</span><span class="token number">5</span><span class="token punctuation">,</span> <span class="token number">6</span><span class="token punctuation">]</span><span class="token punctuation">]</span><span class="token punctuation">)</span>  
<span class="token keyword">print</span><span class="token punctuation">(</span>arr1<span class="token punctuation">)</span>  
arr2 <span class="token operator">=</span> np<span class="token punctuation">.</span>array<span class="token punctuation">(</span><span class="token punctuation">[</span><span class="token punctuation">[</span><span class="token number">7</span><span class="token punctuation">,</span> <span class="token number">8</span><span class="token punctuation">]</span><span class="token punctuation">,</span> <span class="token punctuation">[</span><span class="token number">9</span><span class="token punctuation">,</span> <span class="token number">10</span><span class="token punctuation">]</span><span class="token punctuation">,</span> <span class="token punctuation">[</span><span class="token number">11</span><span class="token punctuation">,</span> <span class="token number">12</span><span class="token punctuation">]</span><span class="token punctuation">]</span><span class="token punctuation">)</span>  
<span class="token keyword">print</span><span class="token punctuation">(</span>arr2<span class="token punctuation">)</span>  
<span class="token comment"># 合并两个numpy数组的行，注意使用hstack()方法合并numpy数组，numpy数组应该有相同的行，其中hstack的h表示horizontal水平的  </span>
<span class="token keyword">print</span><span class="token punctuation">(</span>f<span class="token string">'hstack()方法：arr1和arr2按照行合并：\n{np.hstack((arr1, arr2))}'</span><span class="token punctuation">)</span>  
<span class="token comment"># 合并两个numpy数组，其中axis=1表示合并两个numpy数组的行  </span>
<span class="token keyword">print</span><span class="token punctuation">(</span>f<span class="token string">'np.concatenate方法合并行：\n{np.concatenate((arr1, arr2), axis=1)}'</span><span class="token punctuation">)</span>  
<span class="token comment"># 合并两个numpy数组的列，注意使用vstack()方法合并numpy数组，numpy数组应该有相同的列，其中vstack的v表示vertical垂直的  </span>
<span class="token keyword">print</span><span class="token punctuation">(</span>f<span class="token string">'vstack()方法：arr1和arr2按照列合并：\n{np.vstack((arr1, arr2))}'</span><span class="token punctuation">)</span>  
<span class="token comment"># 合并两个numpy数组，其中axis=0表示合并两个numpy数组的列  </span>
<span class="token keyword">print</span><span class="token punctuation">(</span>f<span class="token string">'np.concatenate方法合并列：\n{np.concatenate((arr1, arr2), axis=0)}'</span><span class="token punctuation">)</span>
</code></pre>
<h1 id="八、创建numpy数组">八、创建numpy数组</h1>

<table>
<thead>
<tr>
<th>方法</th>
<th>详解</th>
</tr>
</thead>
<tbody>
<tr>
<td>array()</td>
<td>将列表转换为数组，可选择显式指定dtype</td>
</tr>
<tr>
<td>arange()</td>
<td>range的numpy版，支持浮点数</td>
</tr>
<tr>
<td>linspace()</td>
<td>类似arange()，第三个参数为数组长度</td>
</tr>
<tr>
<td>zeros()</td>
<td>根据指定形状和dtype创建全0数组</td>
</tr>
<tr>
<td>ones()</td>
<td>根据指定形状和dtype创建全1数组</td>
</tr>
<tr>
<td>eye()</td>
<td>创建单位矩阵</td>
</tr>
<tr>
<td>empty()</td>
<td>创建一个元素全随机的数组</td>
</tr>
<tr>
<td>reshape()</td>
<td>重塑形状</td>
</tr>
</tbody>
</table><pre class=" language-python"><code class="prism  language-python">arr <span class="token operator">=</span> np<span class="token punctuation">.</span>array<span class="token punctuation">(</span><span class="token punctuation">[</span><span class="token number">1</span><span class="token punctuation">,</span> <span class="token number">2</span><span class="token punctuation">,</span> <span class="token number">3</span><span class="token punctuation">]</span><span class="token punctuation">,</span>dtype<span class="token operator">=</span>np<span class="token punctuation">.</span>float32<span class="token punctuation">)</span>  
<span class="token keyword">print</span><span class="token punctuation">(</span>arr<span class="token punctuation">)</span>  
<span class="token comment"># 构造0-9的ndarray数组  </span>
<span class="token keyword">print</span><span class="token punctuation">(</span>np<span class="token punctuation">.</span>arange<span class="token punctuation">(</span><span class="token number">10</span><span class="token punctuation">)</span><span class="token punctuation">)</span>  
<span class="token comment"># 构造1-4的ndarray数组  </span>
<span class="token keyword">print</span><span class="token punctuation">(</span>np<span class="token punctuation">.</span>arange<span class="token punctuation">(</span><span class="token number">1</span><span class="token punctuation">,</span> <span class="token number">5</span><span class="token punctuation">)</span><span class="token punctuation">)</span>  
<span class="token comment"># 构造1-19且步长为2的ndarray数组  </span>
<span class="token keyword">print</span><span class="token punctuation">(</span>np<span class="token punctuation">.</span>arange<span class="token punctuation">(</span><span class="token number">1</span><span class="token punctuation">,</span> <span class="token number">20</span><span class="token punctuation">,</span> <span class="token number">2</span><span class="token punctuation">)</span><span class="token punctuation">)</span>  
<span class="token comment"># 构造一个等差数列，取头也取尾，从0取到20，取5个数  </span>
<span class="token keyword">print</span><span class="token punctuation">(</span>np<span class="token punctuation">.</span>linspace<span class="token punctuation">(</span><span class="token number">0</span><span class="token punctuation">,</span> <span class="token number">20</span><span class="token punctuation">,</span> <span class="token number">5</span><span class="token punctuation">)</span><span class="token punctuation">)</span>  
<span class="token comment"># 构造一个等比数列，从10**0取到10**20，取5个数  </span>
<span class="token keyword">print</span><span class="token punctuation">(</span>np<span class="token punctuation">.</span>logspace<span class="token punctuation">(</span><span class="token number">0</span><span class="token punctuation">,</span> <span class="token number">20</span><span class="token punctuation">,</span> <span class="token number">5</span><span class="token punctuation">)</span><span class="token punctuation">)</span>  
<span class="token comment"># 构造3*4的全0numpy数组  </span>
<span class="token keyword">print</span><span class="token punctuation">(</span>np<span class="token punctuation">.</span>zeros<span class="token punctuation">(</span><span class="token punctuation">(</span><span class="token number">3</span><span class="token punctuation">,</span> <span class="token number">4</span><span class="token punctuation">)</span><span class="token punctuation">)</span><span class="token punctuation">)</span>  
<span class="token comment"># 构造3*4的全1numpy数组  </span>
<span class="token keyword">print</span><span class="token punctuation">(</span>np<span class="token punctuation">.</span>ones<span class="token punctuation">(</span><span class="token punctuation">(</span><span class="token number">3</span><span class="token punctuation">,</span> <span class="token number">4</span><span class="token punctuation">)</span><span class="token punctuation">)</span><span class="token punctuation">)</span>  
<span class="token comment"># 构造3个主元的单位numpy数组  </span>
<span class="token keyword">print</span><span class="token punctuation">(</span>np<span class="token punctuation">.</span>eye<span class="token punctuation">(</span><span class="token number">3</span><span class="token punctuation">)</span><span class="token punctuation">)</span>  
<span class="token comment"># 构造一个4*4的随机numpy数组，里面的元素是随机生成的  </span>
<span class="token keyword">print</span><span class="token punctuation">(</span>np<span class="token punctuation">.</span>empty<span class="token punctuation">(</span><span class="token punctuation">(</span><span class="token number">4</span><span class="token punctuation">,</span> <span class="token number">4</span><span class="token punctuation">)</span><span class="token punctuation">)</span><span class="token punctuation">)</span>  
<span class="token comment"># reshape  </span>
arr <span class="token operator">=</span> np<span class="token punctuation">.</span>ones<span class="token punctuation">(</span><span class="token punctuation">[</span><span class="token number">2</span><span class="token punctuation">,</span> <span class="token number">2</span><span class="token punctuation">]</span><span class="token punctuation">,</span> dtype<span class="token operator">=</span><span class="token builtin">int</span><span class="token punctuation">)</span>  
<span class="token keyword">print</span><span class="token punctuation">(</span>arr<span class="token punctuation">.</span>reshape<span class="token punctuation">(</span><span class="token number">4</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">)</span><span class="token punctuation">)</span>
</code></pre>


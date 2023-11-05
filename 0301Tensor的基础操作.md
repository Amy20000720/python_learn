---


---

<ul>
<li class="task-list-item"><input type="checkbox" class="task-list-item-checkbox" disabled=""> 2023年11月3日第一次创建</li>
<li>[ ]</li>
</ul>
<hr>
<p>参考链接：<br>
<a href="https://www.cnblogs.com/nickchen121/p/10807564.html">1、nick</a></p>
<hr>
<h1 id="一、tensor的引入">一、tensor的引入</h1>
<p>tensor：张量（一维：向量、二维：矩阵、三维：图片、…）</p>
<ul>
<li>如果从接口的角度，对tensor的操作可以分为两类：
<ul>
<li><code>torch.function</code>，如<code>torch.save</code></li>
<li><code>tensor.function</code>，如<code>tensor.view</code><br>
<strong>对于这两种接口方法，大多数时候都是等价的，如<code>torch.sum(a,b)</code>和<code>a.sum(b)</code></strong></li>
</ul>
</li>
<li>从存储的角度讲，对tensor的操作也可以分为两类：
<ul>
<li><code>a.add(b)</code>，不会修改a自身的数据，加法的结果会返回一个新的tensor</li>
<li><code>a.add_(b)</code>，会修改a自身的数据，也就是说加法的结果存在a中<br>
<strong>函数名以_结尾的都是修改调用者自身的数据。</strong></li>
</ul>
</li>
</ul>
<h1 id="二、创建tensor">二、创建tensor</h1>

<table>
<thead>
<tr>
<th>函数</th>
<th>功能</th>
<th>例子</th>
</tr>
</thead>
<tbody>
<tr>
<td>Tensor(size)</td>
<td>基础构造函数</td>
<td>t.Tensor(2,3)  # 指定形状构建2*3维的张量</td>
</tr>
<tr>
<td>ones(size)</td>
<td>全1的Tensor</td>
<td>t.ones(10,1)</td>
</tr>
<tr>
<td>zeros(*sizes)</td>
<td>全0的Tensor</td>
<td>t.zeros(10,1)</td>
</tr>
<tr>
<td>eye(size)</td>
<td>对角矩阵（对角线为1，其他为0，不要求行列一致）</td>
<td>t.eyes(3,4)</td>
</tr>
<tr>
<td>arange(s,e,step)</td>
<td>从s到e，步长为step（<mark>顾头不顾腚</mark>）</td>
<td>t.arange(0,10,2)&gt;&gt;&gt;tensor([0, 2, 4, 6, 8])</td>
</tr>
<tr>
<td>linspace(s,e,step)</td>
<td>从s到e，均匀分成step份（<mark>顾头又顾腚</mark>）</td>
<td>t.linspace(0,10,5)&gt;&gt;&gt;tensor([ 0.0000,  2.5000,  5.0000,  7.5000, 10.0000])</td>
</tr>
<tr>
<td>rand(size)</td>
<td>返回一个或一组服从“0~1”<strong>均匀分布</strong>的随机样本值。随机样本取值范围是[0,1)，不包括1</td>
<td>t.rand(5)&gt;&gt;&gt;tensor([0.0444, 0.5292, 0.8150, 0.6439, 0.5347])</td>
</tr>
<tr>
<td>randn(size)</td>
<td>返回一个或一组服从<span class="katex--inline"><span class="katex"><span class="katex-mathml"><math xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>N</mi><mo stretchy="false">(</mo><mn>0</mn><mo separator="true">,</mo><mn>1</mn><mo stretchy="false">)</mo></mrow><annotation encoding="application/x-tex">N(0,1)</annotation></semantics></math></span><span class="katex-html" aria-hidden="true"><span class="base"><span class="strut" style="height: 1em; vertical-align: -0.25em;"></span><span class="mord mathnormal" style="margin-right: 0.10903em;">N</span><span class="mopen">(</span><span class="mord">0</span><span class="mpunct">,</span><span class="mspace" style="margin-right: 0.166667em;"></span><span class="mord">1</span><span class="mclose">)</span></span></span></span></span><strong>标准正态分布</strong>的随机样本值</td>
<td>t.rand(5)&gt;&gt;&gt;tensor([-0.6638,  1.3208, -1.6684,  1.3031, -0.1184])</td>
</tr>
</tbody>
</table><ul>
<li>normal的用法：</li>
</ul>
<pre class=" language-python"><code class="prism  language-python"><span class="token comment"># g = t.arange(1,0,-0.1)</span>
<span class="token comment"># g</span>
<span class="token comment"># tensor([1.0000, 0.9000, 0.8000, 0.7000, 0.6000, 0.5000, 0.4000, 0.3000, 0.2000, 0.1000])</span>
normal_1 <span class="token operator">=</span> t<span class="token punctuation">.</span>normal<span class="token punctuation">(</span>mean<span class="token operator">=</span>t<span class="token punctuation">.</span>arange<span class="token punctuation">(</span><span class="token number">0</span><span class="token punctuation">.</span><span class="token punctuation">,</span><span class="token number">10</span><span class="token punctuation">.</span><span class="token punctuation">)</span><span class="token punctuation">,</span>std<span class="token operator">=</span>t<span class="token punctuation">.</span>arange<span class="token punctuation">(</span><span class="token number">1</span><span class="token punctuation">,</span><span class="token number">0</span><span class="token punctuation">,</span><span class="token operator">-</span><span class="token number">0.1</span><span class="token punctuation">)</span><span class="token punctuation">)</span>
normal_1
<span class="token operator">&gt;&gt;</span><span class="token operator">&gt;</span>tensor<span class="token punctuation">(</span><span class="token punctuation">[</span><span class="token operator">-</span><span class="token number">1.4051</span><span class="token punctuation">,</span> <span class="token operator">-</span><span class="token number">0.0122</span><span class="token punctuation">,</span>  <span class="token number">3.1039</span><span class="token punctuation">,</span>  <span class="token number">5.1970</span><span class="token punctuation">,</span>  <span class="token number">3.4300</span><span class="token punctuation">,</span>  <span class="token number">5.2285</span><span class="token punctuation">,</span>  <span class="token number">6.8888</span><span class="token punctuation">,</span>  <span class="token number">7.6401</span><span class="token punctuation">,</span>
         <span class="token number">8.4307</span><span class="token punctuation">,</span>  <span class="token number">9.1010</span><span class="token punctuation">]</span><span class="token punctuation">)</span>
<span class="token comment"># 1、mean和std必须是浮点数</span>
<span class="token comment"># 2、mean=tensor([0., 1., 2., 3., 4., 5., 6., 7., 8., 9.])-&gt;shape:(1,9)</span>
<span class="token comment"># 	std=tensor([1.0000, 0.9000, 0.8000, 0.7000, 0.6000, 0.5000, 0.4000, 0.3000, 0.2000, 0.1000])-&gt;shape:(1,9)</span>
<span class="token comment"># attr:`mean` and :attr:`std` don't need to match, but the</span>
<span class="token comment">#    total number of elements in each tensor need to be the same.</span>
    <span class="token punctuation">.</span><span class="token punctuation">.</span> note<span class="token punctuation">:</span><span class="token punctuation">:</span> When the shapes do <span class="token operator">not</span> match<span class="token punctuation">,</span> the shape of <span class="token punctuation">:</span>attr<span class="token punctuation">:</span>`mean`
              <span class="token keyword">is</span> used <span class="token keyword">as</span> the shape <span class="token keyword">for</span> the returned output tensor
normal_2 <span class="token operator">=</span> t<span class="token punctuation">.</span>normal<span class="token punctuation">(</span>mean<span class="token operator">=</span>t<span class="token punctuation">.</span>arange<span class="token punctuation">(</span><span class="token number">0</span><span class="token punctuation">.</span><span class="token punctuation">,</span><span class="token number">10</span><span class="token punctuation">.</span><span class="token punctuation">)</span><span class="token punctuation">,</span>std<span class="token operator">=</span><span class="token number">1</span><span class="token punctuation">)</span>
normal_2
<span class="token operator">&gt;&gt;</span><span class="token operator">&gt;</span>tensor<span class="token punctuation">(</span><span class="token punctuation">[</span><span class="token number">1.5183</span><span class="token punctuation">,</span> <span class="token number">1.2169</span><span class="token punctuation">,</span> <span class="token number">1.9359</span><span class="token punctuation">,</span> <span class="token number">2.7978</span><span class="token punctuation">,</span> <span class="token number">4.5578</span><span class="token punctuation">,</span> <span class="token number">6.5942</span><span class="token punctuation">,</span> <span class="token number">6.3975</span><span class="token punctuation">,</span> <span class="token number">7.4200</span><span class="token punctuation">,</span> <span class="token number">8.6795</span><span class="token punctuation">,</span>
        <span class="token number">9.7888</span><span class="token punctuation">]</span><span class="token punctuation">)</span>
normal_3 <span class="token operator">=</span> t<span class="token punctuation">.</span>normal<span class="token punctuation">(</span>mean<span class="token operator">=</span><span class="token number">5</span><span class="token punctuation">.</span><span class="token punctuation">,</span>std<span class="token operator">=</span><span class="token number">1</span><span class="token punctuation">.</span><span class="token punctuation">,</span>size<span class="token operator">=</span><span class="token punctuation">(</span><span class="token number">2</span><span class="token punctuation">,</span><span class="token number">5</span><span class="token punctuation">)</span><span class="token punctuation">)</span>
normal_3
<span class="token operator">&gt;&gt;</span><span class="token operator">&gt;</span>tensor<span class="token punctuation">(</span><span class="token punctuation">[</span><span class="token punctuation">[</span><span class="token number">4.8072</span><span class="token punctuation">,</span> <span class="token number">5.3175</span><span class="token punctuation">,</span> <span class="token number">3.8454</span><span class="token punctuation">,</span> <span class="token number">5.2074</span><span class="token punctuation">,</span> <span class="token number">4.9846</span><span class="token punctuation">]</span><span class="token punctuation">,</span>
        <span class="token punctuation">[</span><span class="token number">5.7886</span><span class="token punctuation">,</span> <span class="token number">5.1492</span><span class="token punctuation">,</span> <span class="token number">4.3105</span><span class="token punctuation">,</span> <span class="token number">6.3255</span><span class="token punctuation">,</span> <span class="token number">5.4260</span><span class="token punctuation">]</span><span class="token punctuation">]</span><span class="token punctuation">)</span>
</code></pre>


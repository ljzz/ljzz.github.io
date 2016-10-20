title: WordPress 给长文章内容分页
categories: 网络工具
tags:
  - 学习
  - 网络工具
id: 180
date: 2014-08-22 21:06:20
---

我们可能会碰到这样一种情况：发布的文章或页面太长，想要把一篇文章分成好几页，有的时候是为了方便用户阅读，有的时候可以说是为了SEO，到底为了什么目的，那是你的事儿了，我们在这里只是告诉你如何实现Wordpress的文章分页功能。

<!--nextpage-->

WordPress系统是内置分页功能的，要实现它极其简单，只需要在你想要分页的地方加入下面的代码即可(注意，是在**文本**编辑模式下)：

_&lt;!--nextpage--&gt;_

但还有一个问题．要让这个代码真正能够实现其分页功能，还需要你所使用的Wordpress主题支持，Wordpress的默认主题是支持的，如果你的主题不支持，那解决方法也很简单，找到你主题文件内的**single.php**里的下面这行代码：

<div class="wp_syntax" style="color: #110000;">
<table>
<tbody>
<tr>
<td class="line_numbers">
<pre style="color: gray;">1
</pre>
</td>
<td class="code">
<pre class="php"><span style="font-weight: bold;">&lt;?php</span> the_content<span style="color: #009900;">(</span><span style="color: #009900;">)</span><span style="color: #339933;">;</span> <span style="font-weight: bold;">?&gt;</span></pre>
</td>
</tr>
</tbody>
</table>
</div>

在这段代码下面加上：

<div class="wp_syntax" style="color: #110000;">
<table>
<tbody>
<tr>
<td class="line_numbers">
<pre style="color: gray;">1
</pre>
</td>
<td class="code">
<pre class="php"><span style="font-weight: bold;">&lt;?php</span> wp_link_pages<span style="color: #009900;">(</span><span style="color: #0000ff;">'before=&lt;div id="page-links"&gt;&amp;after=&lt;/div&gt;'</span><span style="color: #009900;">)</span><span style="color: #339933;">;</span> <span style="font-weight: bold;">?&gt;</span></pre>
</td>
</tr>
</tbody>
</table>
</div>

即可。

如果你想了解更多，请查阅 [wp_link_pages()](http://codex.wordpress.org/Function_Reference/wp_link_pages)

如果你不想每次都切换到文本编辑模式，那你可以 [在 WordPress 编辑器添加“下一页”分页按钮](http://www.wpdaxue.com/add-next-page-button-wordpress-post-editor.html)
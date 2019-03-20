# Git Flavoured Markdown 

## 1. What is GitHub Flavored Markdown?
GitHub Flavored Markdown (GFM), is the dialect of Markdown that is currently supported for user content on github.com and GitHub Enterprise. GFM is a strict superset of CommonMark. 

The complete formal specification can be found at https://github.github.com/gfm/.

See https://jbt.github.io/markdown-editor/ to preview GFM.  
See https://dillinger.io/ to preview common markdown. 

## 2. Markdown Syntaxes
\\ is an Esacpe character

|Format|Markdown Syntax|Alternative Syntax|HTML Equivalent| 
|-|-|-|-|
|Top level Heading|# foo|n/a|\<h1>foo\</h1>| 
|Third level Heading|### foo|n/a|\<h3>foo\</h3>| 
|Sixth level Heading|###### foo|n/a|\<h6>foo\</h6>| 
|Thematic Break|---|___  OR  ***|\<hr>| 
|Quote|>|n/a|\<q>foo\</q>|
|Bold|\*\*foo*\*|n/a|\<b>foo\</b>|
|Italics|\*foo*|n/a|\<i>foo\</i>|
|Highlight|\`foo`|n/a|\<mark>foo\</mark>|
|Strike Through|\~foo~|n/a|\<del>foo\</del>|
|Bullet Point|* foo|- foo  OR  + foo|\<ul>\<li>foo\</li>\</ul>|
|Numbered List|1) foo|1. foo|\<ol>\<li>foo\</li>\</ol>|
|Line Break|`Two Spaces`|n/a|\<br>|
|Fenced Code|\~~~~<br>code<br>\~~~~|n/a|n/a|
|Link Reference|[foo]: /url "title"<br>[foo]|n/a|\<a href="/url" title="title">foo\</a>|
|Table*|\|foo\|foo\|<br>\|-\|-\|-\|<br>\|bar\|bar\||n/a|\<table><br>\<tr>\<th>foo\</th>\<th>foo\</th>\</tr><br>\<tr>\<td>bar\</td>\<td>bar\</td>\</tr><br>\</table>|
|Task List|- [ ] foo <br> - [x] bar|n/a| https://www.w3schools.com/howto/howto_js_todolist.asp|
|Embed Image|![alt text]\(http://url/to/img.png)|n/a|\<img src="http://url/to/img.png" alt="alt text">|

*Columns are left aligned by default with table headings center aligned. (|:-:|) central alignment of column , (|-:|) right alignment of column. 
                     
                               

  



            

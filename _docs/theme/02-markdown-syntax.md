---
title:  "마크다운 Syntax"
date:   2019-03-13
last_modified_at: 2019-03-21
permalink: /docs/markdown-syntax/
---
{{ child.url }}

제가 Note를 작성하면서 필요하다고 생각하는 마크다운 Syntax를 정리하였습니다. 위가 마크다운이고 아래가 실행결과입니다. 나열순서는 ABC 순입니다.

## Blockquotes
```
> Stay hungry. Stay foolish.

> People think focus means saying yes to the thing you've got to focus on.
But that's not what it means at all. It means saying no to the hundred other good ideas that there are. You have to pick carefully. I'm actually as proud of the things we haven't done as the things I have done. Innovation is saying no to 1,000 things.

<cite>Steve Jobs</cite> --- Apple Worldwide Developers' Conference, 1997
{: .small}
```
> Stay hungry. Stay foolish.

> People think focus means saying yes to the thing you've got to focus on.
But that's not what it means at all.
It means saying no to the hundred other good ideas that there are.
You have to pick carefully.
I'm actually as proud of the things we haven't done as the things I have done.
Innovation is saying no to 1,000 things.

<cite>Steve Jobs</cite> --- Apple Worldwide Developers' Conference, 1997
{: .small}

## Codeblock
위아래를 3개의 back quote로 감싼 후 Code라고 기재된 곳에 Code를 입력하시면 아래의 화면이 출력됩니다.
<pre>
```html
Code
```
</pre>
```html
{% raw %}<nav class="pagination" role="navigation">
  {% if page.previous %}
    <a href="{{ site.url }}{{ page.previous.url }}" class="btn" title="{{ page.previous.title }}">Previous article</a>
  {% endif %}
  {% if page.next %}
    <a href="{{ site.url }}{{ page.next.url }}" class="btn" title="{{ page.next.title }}">Next article</a>
  {% endif %}
</nav><!-- /.pagination -->{% endraw %}
```
***
<pre>
```python
Code
```
</pre>
```python
class ArticleQuerySet(models.QuerySet):
    def search(self, query=None):
        qs = self
        if query is not None:
            or_lookup = (Q(title__icontains=query)|
                         Q(content__icontains=query)
                        )
            qs = qs.filter(or_lookup).distinct() # distinct() is often necessary with Q lookups
        return qs
```
***
```
<pre>
Code
</pre>
```
<pre>
.post-title {
	margin: 0 0 5px;
	font-weight: bold;
	font-size: 38px;
	line-height: 1.2;
	and here's a line of some really, really, really, really long text, just to see how the PRE tag handles it and to find out how it overflows;
</pre>

## Header
```
# Header1
## Header2
### Header3
#### Header4
##### Header5
###### Header6
```

## Horizontal Rules
```
***
```
***

## Image
```liquid
{% raw %}{% include figure image_path="/assets/images/book.jpg" alt="this is a placeholder image" caption="This is a figure caption." %}{% endraw %}
```
{% include figure image_path="/assets/images/book.jpg" alt="this is a placeholder image" caption="This is a figure caption." %}

## Linebreaks
```
라인1
라인2

# <br>이나 space 2번
라인1<br>
라인2
```
라인1
라인2

라인1<br>
라인2

## Link Tag
```
This is an example of a [link](https://apple.com "Apple").
```
This is an example of a [link](https://apple.com "Apple").

```
This is an example of a [link][minimal-mistakes]

[minimal-mistakes]: https://github.com/mmistakes/minimal-mistakes
```
This is an example of a [link][minimal-mistakes]

[minimal-mistakes]: https://github.com/mmistakes/minimal-mistakes

## List
```
* List item one
    * List item one
        * List item one
        * List item two
        * List item three
        * List item four
    * List item two
    * List item three
    * List item four
* List item two
* List item three
* List item four
```
* List item one
    * List item one
        * List item one
        * List item two
        * List item three
        * List item four
    * List item two
    * List item three
    * List item four
* List item two
* List item three
* List item four

```
1. List item one
      1. List item one
          1. List item one
          2. List item two
          3. List item three
          4. List item four
      2. List item two
      3. List item three
      4. List item four
2. List item two
3. List item three
4. List item four
```
1. List item one
      1. List item one
          1. List item one
          2. List item two
          3. List item three
          4. List item four
      2. List item two
      3. List item three
      4. List item four
2. List item two
3. List item three
4. List item four

## Notices
```
**Watch out!** This paragraph of text has been [emphasized](#) with the `{: .notice}` class.
{: .notice}

**Watch out!** This paragraph of text has been [emphasized](#) with the `{: .notice--primary}` class.
{: .notice--primary}

**Watch out!** This paragraph of text has been [emphasized](#) with the `{: .notice--info}` class.
{: .notice--info}

**Watch out!** This paragraph of text has been [emphasized](#) with the `{: .notice--warning}` class.
{: .notice--warning}

**Watch out!** This paragraph of text has been [emphasized](#) with the `{: .notice--success}` class.
{: .notice--success}

**Watch out!** This paragraph of text has been [emphasized](#) with the `{: .notice--danger}` class.
{: .notice--danger}
```
**Watch out!** This paragraph of text has been [emphasized](#) with the `{: .notice}` class.
{: .notice}

**Watch out!** This paragraph of text has been [emphasized](#) with the `{: .notice--primary}` class.
{: .notice--primary}

**Watch out!** This paragraph of text has been [emphasized](#) with the `{: .notice--info}` class.
{: .notice--info}

**Watch out!** This paragraph of text has been [emphasized](#) with the `{: .notice--warning}` class.
{: .notice--warning}

**Watch out!** This paragraph of text has been [emphasized](#) with the `{: .notice--success}` class.
{: .notice--success}

**Watch out!** This paragraph of text has been [emphasized](#) with the `{: .notice--danger}` class.
{: .notice--danger}

## Strong Tag
```
This tag shows **bold text**.
```
This tag shows **bold text**.

---
layout: post
title:  "Welcome to Jekyll!"
date:   2019-06-27 08:24:31 -0700
categories: jekyll update
---
The Posts FolderPermalink
The _posts folder is where your blog posts live. You typically write posts in Markdown, HTML is also supported.

Creating PostsPermalink
To create a post, add a file to your _posts directory with the following format:

YEAR-MONTH-DAY-title.MARKUP
Where YEAR is a four-digit number, MONTH and DAY are both two-digit numbers, and MARKUP is the file extension representing the format used in the file. For example, the following are examples of valid post filenames:

2011-12-31-new-years-eve-is-awesome.md
2012-09-12-how-to-write-a-blog.md
All blog post files must begin with front matter which is typically used to set a layout or other meta data. For a simple example this can just be empty:

---
layout: post
title:  "Welcome to Jekyll!"
---

# Welcome

**Hello world**, this is my first Jekyll blog post.

I hope you like it!
ProTip™: Link to other posts
Use the post_url tag to link to other posts without having to worry about the URLs breaking when the site permalink style changes.

Be aware of character sets
Content processors can modify certain characters to make them look nicer. For example, the smart extension in Redcarpet converts standard, ASCII quotation characters to curly, Unicode ones. In order for the browser to display those characters properly, define the charset meta value by including <meta charset="utf-8"> in the  <head> of your layout.

Including images and resourcesPermalink
At some point, you’ll want to include images, downloads, or other digital assets along with your text content. One common solution is to create a folder in the root of the project directory called something like assets, into which any images, files or other resources are placed. Then, from within any post, they can be linked to using the site’s root as the path for the asset to include. The best way to do this depends on the way your site’s (sub)domain and path are configured, but here are some simple examples in Markdown:

Including an image asset in a post:

... which is shown in the screenshot below:
![My helpful screenshot](/assets/screenshot.jpg)
Linking to a PDF for readers to download:

... you can [get the PDF](/assets/mydoc.pdf) directly.
Displaying an index of postsPermalink
Creating an index of posts on another page should be easy thanks to Liquid and its tags. Here’s a simple example of how to create a list of links to your blog posts:

<ul>
  {% for post in site.posts %}
    <li>
      <a href="{{ post.url }}">{{ post.title }}</a>
    </li>
  {% endfor %}
</ul>
You have full control over how (and where) you display your posts, and how you structure your site. You should read more about how templates work with Jekyll if you want to know more.

Note that the post variable only exists inside the for loop above. If you wish to access the currently-rendering page/posts’s variables (the variables of the post/page that has the for loop in it), use the page variable instead.

Categories and TagsPermalink
Jekyll has first class support for categories and tags in blog posts. The difference between categories and tags is a category can be part of the URL for a post whereas a tag cannot.

To use these, first set your categories and tags in front matter:

---
layout: post
title: A Trip
categories: [blog, travel]
tags: [hot, summer]
---
Jekyll makes the categories available to us at site.categories. Iterating over site.categories on a page gives us another array with two items, the first item is the name of the category and the second item is an array of posts in that category.

{% for category in site.categories %}
  <h3>{{ category[0] }}</h3>
  <ul>
    {% for post in category[1] %}
      <li><a href="{{ post.url }}">{{ post.title }}</a></li>
    {% endfor %}
  </ul>
{% endfor %}
For tags it’s exactly the same except the variable is site.tags.

Post excerptsPermalink
You can access a snippet of a posts’s content by using excerpt variable on a post. By default this is the first paragraph of content in the post, however it can be customized by setting a excerpt_separator variable in front matter or _config.yml.

---
excerpt_separator: <!--more-->
---

Excerpt with multiple paragraphs

Here's another paragraph in the excerpt.
<!--more-->
Out-of-excerpt
Here’s an example of outputting a list of blog posts with an excerpt:

<ul>
  {% for post in site.posts %}
    <li>
      <a href="{{ post.url }}">{{ post.title }}</a>
      {{ post.excerpt }}
    </li>
  {% endfor %}
</ul>
DraftsPermalink
Drafts are posts without a date in the filename. They’re posts you’re still working on and don’t want to publish yet. To get up and running with drafts, create a _drafts folder in your site’s root and create your first draft:

|-- _drafts/
|   |-- a-draft-post.md
To preview your site with drafts, run jekyll serve or jekyll build with the --drafts switch. Each will be assigned the value modification time of the draft file for its date, and thus you will see currently edited drafts as the latest posts.

[jekyll-docs]: https://jekyllrb.com/docs/home
[jekyll-gh]:   https://github.com/jekyll/jekyll
[jekyll-talk]: https://talk.jekyllrb.com/

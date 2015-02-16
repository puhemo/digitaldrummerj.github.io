---
layout: post
title: 'Blogging On Github - Part 5 Adding Category Page'
date: 2015-02-15
categories: ['Blogging', 'Github', 'How-To', 'Jekyll']
published: true
---

Welcome to part 5 of the series on blogging on github.  In this lesson we will go through creating a page to show blog post by category.
 
**Lesson Length**:  15 minutes

**Other Lessons in the Series**

* [View Part 1 Getting Started]({{site.url}}/blogging-on-github-part-1/)
* [View Part 2 Creating your first blog post]({{site.url}}/blogging-on-github-part-2-your-first-post/)
* [View Part 3 Adding the ability for readers to comment on your post]({{site.url}}/blogging-on-github-part-3-adding-comments/)
* [View Part 4 Creating additional pages](http://digitaldrummerj.me/blogging-on-github-part-4-creating-additional-pages/)

### Overview

A typical blog has a way for your readers to view posts by either category or date, so that they can look at your archives without having to go through the blog post one by one.  Unfortunately, the Jekyll-Now repository that we cloned your blog from, does not have these pages.  Luckily, these pages are really easy to create.

### Section 1: Creating the Category Page

If you have been following along with the other lessons in the series, this should be familiar to you.

1. Open a web browser and navigate to your [username].github.io repository.

1. Click on the + button to add a new file

    ![Github Plus Button]({{site.url}}/images/github_add_button.png)

1.  Name the file archivebycategory.md

    ![Github Name the New File archivebycategory.md]({{site.url}}/images/github_part_5_archivebycategory_file_name.png)


### Section 2: Adding the Metadata

Add the following front matter to the top of the archivebycategory.md file.

    {% raw %}
        ---
        layout: page
        title: Post by Category
        permalink: /categoryview/
        sitemap: false
        ---
    {% endraw %}

### Section 3: Category List

After the front matter, add the following code to display the categories and the number of post per category.  Each category will link to further down in the page where is will show the post for that category.

    {% raw %}
        <div>
        {% assign categories = site.categories | sort %}
        {% for category in categories %}
         <span class="site-tag">
            <a href="#{{ category | first | slugify }}">
                    {{ category[0] | replace:'-', ' ' }} ({{ category | last | size }})
            </a>
        </span>
        {% endfor %}
        </div>
    {% endraw %}

### Section 4: Blog Post by Category

Next you need to add the code to display the list of blog post by category and sorted by title

    {% raw %}
        <div id="index">

        {% for category in categories %}
        <a name="{{ category[0] }}"></a><h2>{{ category[0] | replace:'-', ' ' }} ({{ category | last | size }}) </h2>
        {% assign sorted_posts = site.posts | sort: 'title' %}
        {% for post in sorted_posts %}
        {%if post.categories contains category[0]%}

          <h3><a href="{{ site.url }}{{ post.url }}" title="{{ post.title }}">{{ post.title }} <p class="date">{{ post.date |  date: "%B %e, %Y" }}</p></a></h3>
           <p>{{ post.excerpt | strip_html | truncate: 160 }}</p>

        {%endif%}
        {% endfor %}

        {% endfor %}
        </div>
    {% endraw %}



###  Section 5: Viewing the Category Page

1. After you have added the above text, scroll to the bottom of the page, add your commit note, and    click the commit button.

    ![Github Commit archivebycategory.md]({{site.url}}/images/github_part_5_commit_archivebycategory.png)

1. To  view the category page, navigate to http://[username].github.io/categoryview

1. Your page should look like the following but with your avatar, site name and description in the header of the page.

    ![category view screenshot]({{ site.url}}/images/github_part_5_archivebycategory_in_browser.png)

1. Right now the page is published but not linked to from anywhere.  In the next section we will add it to the header section of the page.

### Section 6: Adding Category View into Header

Unlike the portfolio page that we created in the last lesson, this time we are not going to add the category page into the menu.  Instead we are going to create a row below the header with a link to the page.

1. Go into the _layouts directory by clicking on _layouts

1. Click on the default.html file to open it.

1. Click on the ![github_edit_button.png]({{site.url}}/images/github_edit_button.png) icon to edit the file.

1. Right after the &lt;/header&gt; tag, add the following html snippet

        {% raw %}
          <div class="container" >
                <div id="archives">
                    browse by <a title="The complete archive of {{ site.name }}'s Blog by category"
                                 href="{{ site.url}}/categoryview">category</a>
                </div>
            </div>
          </div>
        {% endraw %}

1. Scroll down to the bottom, add the commit comment, and click on the commit change button.

    ![Commit default.html changes]({{site.url}}/images/github_part_5_commit_default.png)

1. Now go view your blog's home page at http://[username].github.io/.  You should now see the "browse by category" link in the header.

    ![Blog's Home Page with Browse By Category Link in Header]({{site.url}}/images/github_part_5_browse_by_category_in_header.png)

### Conclusion

With just a few simple steps, you were added the post by category page and put it in the header.  In the next lesson we will add in a new page for browsing blog post by year and month.

### Series Lessons

* [Part 1 Getting Started]({{site.url}}/blogging-on-github-part-1/)
* [Part 2 Creating your first blog post]({{site.url}}/blogging-on-github-part-2-your-first-post/)
* [Part 3 Adding the ability for readers to comment on your post]({{site.url}}/blogging-on-github-part-3-adding-comments/)
* [Part 4 Creating additional pages](http://digitaldrummerj.me/blogging-on-github-part-4-creating-additional-pages/)
* Part 5 Adding a page that list post by category (this lesson)
* Part 6 Adding a page that list post by month
* Part 7 Customizing the theme
* Part 8 Adding a custom Google search
* Part 9 Using your own domain name
* Part 10 How to make change locally and push them to Github
* Part 11 Pro Tips
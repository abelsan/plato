---
layout: base
---
## Page explores ways to include posts on a page

We can get access to the site's posts and other collections by using "site.collections". The object gives you access to document labels - titles for posts.

{% for collection in site.collections %}
    ### Items from {{ collection.label }}
    
    #### Inspect the variables:
    relative_directory: {{ collection.relative_directory }}
    directory: {{ collection.directory }}
    output: {{ collection.output }}

    #### Loop through the labels (titles):
    {% for item in site[collection.label] %}
        * <a href="{{ item.url }}">{{ item.title }}</a>
    {% endfor %}

    #### Limit the list length:
    <ul>
        {% for item in site[collection.label] limit:2 %}
         * <a href="{{ item.url }}">{{ item.title }}</a>
        {% endfor %}
    </ul>  
{% endfor %}


### Quick code to get list of posts
{% for post in site.posts %}
    * <a href="{{ post.url }}">{{ post.title }}</a>
{% endfor %}


### List of tags plus the posts for that tag
{% for tag in site.tags %}
  {{ tag[0] }}
    {% for post in tag[1] %}
      * <a href="{{ post.url }}">{{ post.title }}</a>
    {% endfor %}
{% endfor %}

### Post count per tag
{% for tag in site.tags %}
    {% assign t = tag | first %}
    {% assign posts = tag | last %}
        {{t | downcase | replace:" ","-" }} has {{ posts | size }} posts
{% endfor %}


### List of tags - alternate code
{% for tag in site.tags %}
    {% assign t = tag | first %}
    {% assign posts = tag | last %}
    {{ t | downcase }}

    ### List of tags - alternate code
    {% for post in posts %}
    {% if post.tags contains t %}
        <a href="{{ post.url }}">{{ post.title }}</a>
        <span class="date">{{ post.date | date: "%B %-d, %Y"  }}</span>
    {% endif %}
    {% endfor %}
{% endfor %}

### Tags - Horizontal
{% for tag in site.tags %}
    * <a href="#{{ tag[0] | slugify }}" class="post-tag">{{ tag[0] }}</a>
{% endfor %}
---
# By default, content added below the "---" mark will appear in the home page
# To change the home page layout, edit the _layouts/home.html file.
layout: home
---

### Landing Page - for code see index.md
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.  


Link to [list of blog posts and tags](blogs_and_tags.html).
Link to [blog](blog).

<h4>Limit the list length:</h4>
{% for item in site[collection.label] limit:2 %}
        - <a href="{{ item.url }}">{{ item.title }}</a> <br>
{% endfor %}
<br class="py-3">
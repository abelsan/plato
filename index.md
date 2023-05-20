---
# By default, content added below the "---" mark will appear in the home page
# To change the home page layout, edit the _layouts/home.html file.
layout: home
---

### Landing Page
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. 

### Explore linking
{% post_url 2023-01-01-one %}

<ul class="entries">
  {% for post in paginator.posts %}
  <li>
    <a href="{{ post.url }}">
    <h3>{{ post.title }}</h3>
    <p class="blogdate">{{ post.date | date: "%d %B %Y" }}</p>
    <div>{{ post.content |truncatehtml | truncatewords: 60 }}</div>
    </a>
  </li>
  {% endfor %}
</ul>
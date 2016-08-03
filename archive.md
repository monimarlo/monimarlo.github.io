---
layout: page
title: Archivo - Mónica Martínez
permalink: /archive/
---

<script type="text/javascript">
function handle_selection(element) {
    window.location = element.value;
    if (element.value != "#all") {
        $('.catbloc_showing_all').removeClass('catbloc_showing_all').addClass('catbloc');
    } else {
        $('.catbloc').removeClass('catbloc').addClass('catbloc_showing_all');
    }
}
</script>

<nav>

    <select id="category_selector" name="Categories" onchange="handle_selection(this);">
        <option value="#all" selected="selected">Todo</option>
        {% for category in site.categories %}
            <option value="#{{ category | first | remove:' ' }}">{{ category | first }}</option>
        {% endfor %}
    </select>
        <!--<a href="#{{ category | first | remove:' ' }}"><strong>{{ category | first }}</strong></a>{% if forloop.last %}.{% else %}, {% endif %}-->

</nav>

{% for category in site.categories %}
<div class="catbloc_showing_all" id="{{ category | first | remove:' ' }}">
    <h1 class="category_header">{{ category | first }}</h1>
         
    <ul class="archive_posts">
        {% for posts in category %}
            {% for post in posts %}
                {% if post.url %}
                    <li>
                        <span class="date">{{ post.date | date: '%d/%m/%y' }}&raquo; </span><a href="{{ post.url }}">{{ post.title }}</a>
                    </li>
                {% endif %}
            {% endfor %}
        {% endfor %}
    </ul>
</div>
{% endfor %}

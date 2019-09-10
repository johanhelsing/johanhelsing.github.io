{% for  post in site.posts %}

## [{{ post.title }}]({{ post.url }})

{{ post.excerpt}}

[Read more]({{ post.url }})

{% endfor %}

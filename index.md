{% for  post in site.posts reversed %}

## [{{ post.title }}]({{ post.url }})

{{ post.excerpt}}

[Read more]({{ post.url }})

{% endfor %}

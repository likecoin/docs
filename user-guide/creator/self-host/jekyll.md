---
description: How to embed LikeCoin button into Jekyll
---

# Jekyll

Thanks to the user [PinGuの独り言](https://pingu.moe/2020/01/integrate-likebutton-with-jekyll/) for providing the tutorial.

Before adding the LikeCoin button, please [register a Liker ID](../../liker-id/).

Follow the steps below:

### Config liker\_id in \_config.yml  <a href="#cong-configyml-she-ding-likerid" id="cong-configyml-she-ding-likerid"></a>

Add `liker_id` in `_config.yml`  and change \[LikerID] into your Liker ID. It should look like this:

```
# Enter your Liker ID to enable LikeCoin button
liker_id: [LikerID]
```

Define the variables in `_config.yml`. The variables can be obtained in the site object using `{{site.liker_id}}`

```
https://button.like.co/in/embed/{{site.liker_id}}/button?referrer={{ page.url | absolute_url | cgi_escape }}
```

### Insert the iframe <a href="#cha-ru-iframe" id="cha-ru-iframe"></a>

Develop the LikeCoin button HTML and use the following code to insert the iframe:

```
{% raw %}
{% if site.liker_id %}
<iframe
  src="https://button.like.co/in/embed/{{site.liker_id}}/button?referrer={{ page.url | absolute_url | cgi_escape }}">
</iframe>
{% endif %}
{% endraw %}
```

Use if to inspect if `liker_id` exists. Then add the code to the post template, find a place near the end of the post template and add `{% include likeco.html %}` to include the LikeCoin button.

Build the website, and the LikeCoin button will be added at the end of each article. However, the size may need adjustment. The LikeCoin button will adapt itself to a width of 485px and a height of 240px. Use the following code to align it to the middle and hide the scroll bar.

```
{% raw %}
{% if site.liker_id %}
<iframe
  style="width: 100%; max-width: 485px; height: 240px; margin: auto; overflow: hidden; display: block;"
  src="https://button.like.co/in/embed/{{site.liker_id}}/button?referrer={{ page.url | absolute_url | cgi_escape }}">
</iframe>
{% endif %}
{% endraw %}
```

---
description: How to embed LikeCoin button into Jekyll
---

# Jekyll

Thanks to the user [PinGuの独り言](https://pingu.moe/2020/01/integrate-likebutton-with-jekyll/) for the tutorial.

Before adding the LikeCoin button, please [register a Liker ID](https://docs.like.co/user-guide/liker-id/register).

### Config liker\_id in \_config.yml  <a id="&#x5F9E;_configyml&#x8A2D;&#x5B9A;liker_id"></a>

Add `liker_id` in `_config.yml` , and change \[LikerID\] into your Liker ID

```text
# Enter your Liker ID to enable LikeCoin button
liker_id: [LikerID]
```

Define the variables in `_config.yml` can be obtained in the site object, which is `{{site.liker_id}}`

```text
https://button.like.co/in/embed/{{site.liker_id}}/button?referrer={{ page.url | absolute_url | cgi_escape }}
```

### Insert iframe <a id="&#x63D2;&#x5165;iframe"></a>

Develop the LikeCoin button HTML

```text
{% if site.liker_id %}
<iframe
  src="https://button.like.co/in/embed/{{site.liker_id}}/button?referrer={{ page.url | absolute_url | cgi_escape }}">
</iframe>
{% endif %}
```

Use if to inspect if `liker_id` exists. Then add the code into post template, find a place near the end and add `{% include likeco.html %}`

Build it, the LikeCoin button is already at the end of each article, but the size has to be adjusted. LikeCoin button will adapt itself to 485px weight\*240px height. Use the following code to align middle and hide the scroll bar.

```text
{% if site.liker_id %}
<iframe
  style="width: 100%; max-width: 485px; height: 240px; margin: auto; overflow: hidden; display: block;"
  src="https://button.like.co/in/embed/{{site.liker_id}}/button?referrer={{ page.url | absolute_url | cgi_escape }}">
</iframe>
{% endif %}
```


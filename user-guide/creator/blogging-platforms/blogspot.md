---
description: >-
  Using JavaScript in Blogspot to add LikeCoin button to end of the article or
  sidebar
---

# Blogspot

Thanks to [浩剛](https://danieltw.net/archives/2444) for creating the code to embed the LikeCoin button into every blog post by adding JavaScript to the sidebar tool or changing the blog theme.

Before adding the LikeCoin button, please [register a Liker ID](../../liker-id/).

### **LikeCoin button on the sidebar**

In the page settings, select a position to add the 'HTML/JavaScript' widget. Paste the following JavaScript code into it and change the \[LikerID] to your Liker ID, then save it. The LikeCoin button will appear automatically.

```
<script type="text/javascript">
    document.write("<iframe scrolling='no' frameborder='0' sandbox='allow-scripts allow-same-origin allow-popups allow-popups-to-escape-sandbox allow-storage-access-by-user-activation' style='height: 212px; width: 100%;' src='https://button.like.co/in/embed/[LikerID]/button?referrer="+encodeURIComponent(location.href.split("?")[0].split("#")[0])+"'></iframe>");
</script>
```

### **LikeCoin button at the end of each article**

Go to 'Theme' and click 'Edit HTML'. Search for **data:post.body**, and when you see `</div>`, insert the following source code, replacing \[LikerID] with your Liker ID:\


```
<b:if cond='data:blog.pageType == "item"'>
    <script type="text/javascript">
        document.write("<iframe scrolling='no' frameborder='0' sandbox='allow-scripts allow-same-origin allow-popups allow-popups-to-escape-sandbox allow-storage-access-by-user-activation' style='height: 212px; width: 100%;' src='https://button.like.co/in/embed/[LikerID]/button?referrer="+encodeURIComponent(location.href.split("?")[0].split("#")[0])+"'></iframe>");
    </script>
</b:if>
```

Example of data:post.body below:

```
<!-- Then use the post body as the schema.org description, for good G+/FB snippeting. -->
<div class='post-body entry-content' expr:id='"post-body-" + data:post.id' expr:itemprop='(data:blog.metaDescription ? "" : "description ") + "articleBody"'>
  <data:post.body/>
  <div style='clear: both;'/> <!-- clear for photos floats -->
</div>
```

Add the source code after the closing `</div>` tag, so it becomes:

```
<!-- Then use the post body as the schema.org description, for good G+/FB snippeting. -->
<div class='post-body entry-content' expr:id='"post-body-" + data:post.id' expr:itemprop='(data:blog.metaDescription ? "" : "description ") + "articleBody"'>
  <data:post.body/>
  <div style='clear: both;'/> <!-- clear for photos floats -->
</div>

<b:if cond='data:blog.pageType == "item"'>
    <script type="text/javascript">
        document.write("<iframe scrolling='no' frameborder='0' sandbox='allow-scripts allow-same-origin allow-popups allow-popups-to-escape-sandbox allow-storage-access-by-user-activation' style='height: 212px; width: 100%;' src='https://button.like.co/in/embed/[LikerID]/button?referrer="+encodeURIComponent(location.href.split("?")[0].split("#")[0])+"'></iframe>");
    </script>
</b:if>
```

If there are two instances of **data:post.body** in the 'Edit HTML' section, you have to edit both because one is for desktop and the other is for mobile. Please note that you have to change to "Custom" for the mobile version in order for the LikeCoin button to display.

\-------------------------

If your other blog services support a change of theme, you may try to add a LikeCoin button by this method.

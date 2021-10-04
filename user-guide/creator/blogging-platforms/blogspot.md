---
description: >-
  Using JavaScript in Blogspot to add LikeCoin button to end of the article or
  sidebar
---

# Blogspot

Thanks [浩剛](https://danieltw.net/archives/2444) for creating the code to embed LikeCoin button into every blog post by adding Javascript to the sidebar tool or change the blog theme.

Before adding the LikeCoin button, please [register a Liker ID](../../liker-id/).

### **LikeCoin button on sidebar**

On page settings, select a position to add "HTML/JavaScript", paste the following Javascript code into it and change the \[LikerID\] to your Liker ID then save it. The LikeCoin button will appear automatically.

```text
<script type="text/javascript">
    document.write("<iframe scrolling='no' frameborder='0' sandbox='allow-scripts allow-same-origin allow-popups allow-popups-to-escape-sandbox allow-storage-access-by-user-activation' style='height: 212px; width: 100%;' src='https://button.like.co/in/embed/[LikerID]/button?referrer="+encodeURIComponent(location.href.split("?")[0].split("#")[0])+"'></iframe>");
</script>
```

### **LikeCoin button at the end of each article**

Go to "Theme" and click "Edit HTML" and search for **data:post.body**, carriage return when seeing `</div>` then add the following source code, and change the \[LikerID\] to your Liker ID:  


```text
<b:if cond='data:blog.pageType == "item"'>
    <script type="text/javascript">
        document.write("<iframe scrolling='no' frameborder='0' sandbox='allow-scripts allow-same-origin allow-popups allow-popups-to-escape-sandbox allow-storage-access-by-user-activation' style='height: 212px; width: 100%;' src='https://button.like.co/in/embed/[LikerID]/button?referrer="+encodeURIComponent(location.href.split("?")[0].split("#")[0])+"'></iframe>");
    </script>
</b:if>
```

data:post.body example below

```text
<!-- Then use the post body as the schema.org description, for good G+/FB snippeting. -->
<div class='post-body entry-content' expr:id='"post-body-" + data:post.id' expr:itemprop='(data:blog.metaDescription ? "" : "description ") + "articleBody"'>
  <data:post.body/>
  <div style='clear: both;'/> <!-- clear for photos floats -->
</div>
```

adding source code after `</div>` and become

```text
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

If there are two **data:post.body** when "Edit HTML", You have to edit both because one is for desktop and the other is for mobile. Please note that you have to change to "Custom" for the mobile version in order for the LikeCoin button to display.

-------------------------

If your other blog services support a change of theme, you may try to add a LikeCoin button by this method.


---
description: How to embed LikeCoin button into Hugo
---

# Hugo

Thanks to the user [Wancat](https://www.wancat.cc/post/hugo-install-likecoin/) for the tutorial.

Before adding the LikeCoin button, please [register a Liker ID](https://docs.like.co/user-guide/liker-id/register).

Choose a theme for your website first, the following is an example of [CleanWhite](https://themes.gohugo.io/hugo-theme-cleanwhite). 

Hugo allows users to use custom Layout in order to change the website design without altering the theme, LikeCoin button can be added with this function.

The 1st step is to copy the post template, copy the `layouts` folder in `theme` to the directory of the repository

```text
cp -r theme/YOUR_THEME/layouts/ .
```

Hugo allows users to create simple templates with [Partial Templates](https://gohugo.io/templates/partials/) and embed it into a page. Create `likecoin.html` in `partials` folder of `layouts`, fill in the following code. Words to encourage clapping of LikeCoin button can also be included in HTML format

```text
<iframe class="LikeCoin" height="235" src="https://button.like.co/in/embed/{{ .Site.Params.likerID }}/button?referrer={{ .Permalink }}" width="100%" frameborder=0></iframe>
```

 Add the following code to `config.toml`, and change \[LikerID\] to your Liker ID

```text
[[params]]
	likerID = "likerID"
```

Then edit the post template, it is usually in `_default/single.html`. This is a Go Template, suggest to put the code after `{{ .Content }}`, LikeCoin button will appear at the end of the article

```text
{{ partial "likecoin.html" . }}
```

Hugo is going to render this partial to your posts. Remember to add the ".", otherwise the LikeCoin template cannot read the data. In fact it is not necessary to modify the original Hugo theme

Last step is to run `hugo server` and preview your website.


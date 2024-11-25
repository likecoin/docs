---
description: How to embed LikeCoin button into Hugo
---

# Hugo

Thanks to the user [Wancat](https://www.wancat.cc/post/hugo-install-likecoin/) for providing the tutorial.

Before adding the LikeCoin button, please [register a Liker ID](../../liker-id/).

Choose a theme for your website first. The following is an example using the [CleanWhite](https://themes.gohugo.io/hugo-theme-cleanwhite) theme.

Hugo allows users to use custom layouts to change the website design without altering the theme. The LikeCoin button can be added using this function. Follow the steps below:

Copy the post template by copying the `layouts` folder from your `theme` to the repository directory:

```
cp -r theme/YOUR_THEME/layouts/ .
```

Hugo allows users to create simple templates with [Partial Templates](https://gohugo.io/templates/partials/) and embed them into a page. Create a file named `likecoin.html` in `partials` folder of the `layouts` directory. Fill in the following code. You can also include words to encourage clapping the LikeCoin button in HTML format:

```
<iframe class="LikeCoin" height="235" src="https://button.like.co/in/embed/{{ .Site.Params.likerID }}/button?referrer={{ .Permalink }}" width="100%" frameborder=0></iframe>
```

&#x20;Add the following code to your `config.toml` file and change \[LikerID] to your Liker ID:

```
[[params]]
	likerID = "likerID"
```

Edit the post template, which is usually located in `_default/single.html`. This is a Go Template. It is suggested to place the code after `{{ .Content }}` so that the LikeCoin button will appear at the end of the article:

```
{{ partial "likecoin.html" . }}
```

Hugo will render this partial for your posts. Remember to include the "." in the code, otherwise the LikeCoin template won't be able to read the data. In fact, it is not necessary to modify the original Hugo theme.

The last step is to run `hugo server` to preview your website.

By following these steps, the LikeCoin button will be added to your website.

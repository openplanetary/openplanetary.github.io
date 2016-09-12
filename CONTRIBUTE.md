# Publishing on the OpenPlanetary Blog

To publish on the OpenPlanetary Blog, you need at have a GitHub account.

At the moment, only the OP GitHub [op-team](https://github.com/orgs/openplanetary/teams/op-team) have write permission to the openplanetary.github.io repository, but any GitHub users can make a pull request to upload a post file in the [_posts](https://github.com/openplanetary/newwebsite/tree/master/_posts) directory.

It is possible to post a blog (feel free to correct update) with any of those options:

* Creating directly a file following the [template](https://github.com/openplanetary/tree/master/_drafts/yyyy-mm-dd-post-template.markdown)
* Pulling, creating, committing and pushing (once in the OP GitHub op-team, please ask if needed)
* Forking and creating a pull request with your additional post in.

Note: Consider using the `_drafts` directory for drafting your blog post first.

## Topics and guidelines

Topics are not limited but include planetary data, tools, workflow, science, community events; for example: availability of planetary data, including information on how the data are found, downloaded, processed, and used for cartography and scientific analysis; trends in data storage and rapid access; analysis and visualization tools using current and new algorithms and methods.

## Post files

Post files are located in the [_posts](https://github.com/openplanetary/newwebsite/tree/master/_posts) directory. These files are generally Markdown or HTML, but can be other formats with the proper converter installed. All posts must have YAML Front Matter, and they will be converted from their source format into an HTML page that is part of your static site.

File naming scheme is: `YYYY-MM-DD-post-title.markdown`, where `YYYY-MM-DD` is the date at which the post will be published.

More info at [https://jekyllrb.com/docs/posts/](https://jekyllrb.com/docs/posts/)

### Header

They must begin with a mandatory header, called YAML front matter block, as follows:

```
---
layout:        post
title:         "The title of your post"
subtitle:      "The subtitle of your post"
authors:       member_id
header-img:    "img/post-bg-05.jpg"
category:      Category1
tags:          [tag1, tag2, tag3]
slack_channel: channel1
---
```

* `layout`: specifies layout to be use for generating the HTML post: always `post`
* `title`: specifies title of your post. E.g.: "My awesome workflow"
* `subtitle`: specifies the subtitle of your post. It appears on the post header, and recent posts page.
* `author`: specifies the post author (only one per post) through a `member_id`, defined in [_data/members.yml](https://github.com/openplanetary/newwebsite/tree/master/_data/members.yml). If empty, "OpenPlanetary Team" author will be used. List of authors (members with a GitHub account) is available [here](http://openplanetary.github.io/newwebsite/blog/authors).
* `header-img` [Optional]: Default post header image is [img/page-bg.jpg](https://openplanetary.github.io/newwebsite/img/page-bg.jpg). Eg.: "img/post-bg-05.jpg".
* `category`: specifies the post category. There is only one category per post: `Data`, `Tools`, `Science`, `Community`
* `tags`: There can be several tags per post, e.g: `[ctx, mro, gist, isis3, Python]`. Try to avoid duplicates, look at existing tags [here](https://openplanetary.github.io/newwebsite/blog/tags/) first.
* `slack_channel` [Optional]: specifies Slack channel readers will be directed to to discuss internally with members


### Content

After the header, it’s simply a matter of deciding which format you prefer: Markdown or HTML.
We recommend Markdown. Here is a few resources to get started with format:

* [https://guides.github.com/features/mastering-markdown/](https://guides.github.com/features/mastering-markdown/)
* [http://markdown-guide.readthedocs.io/](http://markdown-guide.readthedocs.io/)
* [http://en.wikipedia.org/wiki/Markdown](http://en.wikipedia.org/wiki/Markdown)
* [http://daringfireball.net/projects/markdown/](http://daringfireball.net/projects/markdown/)

#### Images

Should you have any images in your post, upload in `img/` directory using the `post-` preffix.

#### Gist and Syntax highlighting

The easiest way to achieve automatic syntax highlighting for most programming languages within a post, rather than include a [markdown code block](https://guides.github.com/features/mastering-markdown/), is to use a [gist](https://gist.github.com/), which renders already code and even Jupyter notebooks (.ipynb), e.g. with:

```
{% gist user/dac0f38f4991f8da9fcfe3722728ce16 %}
```

#### Inclusion of Jypyter notebooks

The procedure above is well suited for including Jupyter notebooks, rendering structure, cell content, output imagery and in-line plots. The procedure for including .ipynb files into a post is as follows:

* Create your .ipynb jupyter notebook (e.g. locally on your system)
* Open the .ipynb file with a text editor and copy all the content (it might be a lot, e.g. if you have images encoded) into a new [gist](https://gist.github.com/). Some [Jupyter extension/plugin](https://github.com/ipython-contrib/jupyter_contrib_nbextensions/tree/b29c698394239a6931fa4911440550df214812cb/src/jupyter_contrib_nbextensions/nbextensions/gist_it) might facilitate that.
* Make sure that the filename _in gist_ has a .ipynb extension (so that gist knows to render it correctly).
* Copy user/gistid (see example above) and embed it into your post.

Please note that if you have in addition any markdown code blocks, e.g. above the embedded .ipynb, in order for this procedure to work you should use ``` rather than TAB (see example [here](https://github.com/openplanetary/newwebsite/edit/master/_posts/2016-09-10-w10n.md))

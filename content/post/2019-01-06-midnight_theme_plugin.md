+++
title = "Hugo Midnight Theme Plugin"
description = ""
tags = [
    "development",
]
date = "2019-01-05"
categories = [
    "Development",
]
+++
This new site uses the ["Midnight"](https://themes.gohugo.io/midnight/) theme for Hugo which includes
support for plugins. I decided I wished to embed a twitter feed in the side-bar but had some difficulty getting this to work.

I defined the plugin widget file as follows:

`SITE_ROOT/layouts/partials/sidebar/twitterfeed/widget.html`

Then was trying to get it working with the following toml configuration:
{{< highlight toml >}}
    [params.sidebar.twitterfeed]
        [params.sidebar.twitterfeed.partial]
            path = "sidebar/twitterfeed/widget.html"
            cache = true
{{< /highlight >}}

This failed with an error that it was unable to find the widget. An inspection of the theme suggested I had to define a 'path' element - something the documentation example is not clear on being required:

{{< highlight toml >}}
    [params.sidebar.twitterfeed]
        path = "sidebar/twitterfeed"
        [params.sidebar.twitterfeed.partial]
            path = "sidebar/twitterfeed/widget.html"
            cache = true
{{< /highlight >}}

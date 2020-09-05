---
layout: post
title:  "CVI: Hosting your own alternative dialling instructions"
date:   2020-09-04 08:00:00 +0100
categories: pexip cvi
---

https://docs.pexip.com/admin/teams_intro.htm

When you enable Microsoft Teams integration with Pexip Infinity one of the [final steps](https://docs.pexip.com/admin/teams_connector.htm#authorize_lobby) is to configure the dialling instructions for your users using the `SkypeOnlineConnector` PowerShell module.  The dialling instructions are embedded into a Microsoft Teams invite and enables users to visit a webpage with additional joining instructions for the meeting.

![cvi-invitation-instructions]({{ site.baseurl }}/assets/img/2020-09-04-hosting-your-own-alternate-dialling-instructions/invitation_instructions_784x602.png){:class="img-responsive"}

Pexip Infinity nodes host a default page for these dialling instructions, and this is where you would normally point your users but this default template does not suit everyone (and it is also not supported to edit this default template directly on the Pexip nodes), if you would like to modify this and host your own dialling instructions, follow the steps below.

![pexip-default-cvi-page]({{ site.baseurl }}/assets/img/2020-09-04-hosting-your-own-alternate-dialling-instructions/pexip_default_cvi_page_1289x683.png){:class="img-responsive"}

### Pull the default files from a Pexip node

The files for the default Pexip template are located on the Pexip nodes (transcoding or proxy) in the path below

```
/opt/pexip/share/web/static/dist/web/teams
```

Copy this folder from the Pexip nodes to your local machine

# MacOS

```
scp -r admin@pexip_node:/opt/pexip/share/web/static/dist/web/teams/  /local/directory
```

# Windows

You 

Get-WindowsCapability -Online | ? Name -like 'OpenSSH*'

Name  : OpenSSH.Client~~~~0.0.1.0
State : Installed

You’ll find this post in your `_posts` directory. Go ahead and edit it and re-build the site to see your changes. You can rebuild the site in many different ways, but the most common way is to run `jekyll serve`, which launches a web server and auto-regenerates your site when a file is updated.

Jekyll requires blog post files to be named according to the following format:

`YEAR-MONTH-DAY-title.MARKUP`

Where `YEAR` is a four-digit number, `MONTH` and `DAY` are both two-digit numbers, and `MARKUP` is the file extension representing the format used in the file. After that, include the necessary front matter. Take a look at the source for this post to get an idea about how it works.

Jekyll also offers powerful support for code snippets:

{% highlight ruby %}
def print_hi(name)
  puts "Hi, #{name}"
end
print_hi('Tom')
#=> prints 'Hi, Tom' to STDOUT.
{% endhighlight %}

Check out the [Jekyll docs][jekyll-docs] for more info on how to get the most out of Jekyll. File all bugs/feature requests at [Jekyll’s GitHub repo][jekyll-gh]. If you have questions, you can ask them on [Jekyll Talk][jekyll-talk].

[jekyll-docs]: https://jekyllrb.com/docs/home
[jekyll-gh]:   https://github.com/jekyll/jekyll
[jekyll-talk]: https://talk.jekyllrb.com/

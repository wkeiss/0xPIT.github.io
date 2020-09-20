---
title: "New updates of my site"
layout: post
date: 2020-09-18
tag:
- "2020"
- "blog"
blog: true
---

### Connect a custom domain

From several days ago, I can't reach githu.io pages, like wkeiss.github.io. And I found if there is a custom domain connect to github page, then we can visit it. So I decided to buy and connect a domain to my website.

![github-io-cannt-reach](/assets/images/blog-image/github-io-cannt-reach.jpg)

I choose to buy a domain in Aliyun, since compared to other domain name registrars like namecheap, Gandi, it's more possibly to buy a cheaper domain in China registars. 

After register a domain,  you can follow the help doc to connect domain to your github page: [Managing a custom domain for your GitHub Pages site - GitHub Docs](https://docs.github.com/en/github/working-with-github-pages/managing-a-custom-domain-for-your-github-pages-site). 

Finally, I need to update the site url to the new one after the site can be visit via domain in `_config.yml` file in my github page diretory. So the urls of every pages in my site will be update to new one.

### Add Disqus 

I hope people can comment my blog, though I think almost nobody visits my site, but maybe  someday there will be someone want to leave a comment, so I decided to add [Disuqs](https://disqus.com/) to my site.

First you need to add your site your Disqus account, if you don't have a Disqus account yet, you need to register one firstly. 

If you like me use the [ Jekyll Template](https://github.com/sergiokopplin/indigo) to build your site, you don't need to install disqus into your site. But you should add your site to your disqus account to get your site's short name start from here:https://disqus.com/admin/create/. Then you will head to a select plan page, you can don't buy a plan now, just skip to step 3 configure Disqus buy click "Configure Disqus", and input the inqured info, click 'Complete Setup' in the bottom right corner.

![configure-disqus](/assets/images/blog-image/configure-disqus.jpg)

Head to the https://disqus.com/admin/settings/general/  and click the site you just added, then you can see your site's short name.

![click-the-site-just-added](/assets/images/blog-image/click-the-site-just-added.jpg)

![short-name](/assets/images/blog-image/short-name.jpg)

Finally, add the short name to the  `_config.yml` file, all setup.

### Change the favicon 

Before I did it, I found the relative file and code in my githubpage respository.I need to change the picture I choose to use as favicon into more than 10 different  sizes and I need to named the new size photoes like these show in the files,  how troublesome! 

When I tried to find an easy way to change my favicon, I found [a site to generate favicon quite simplily](https://www.favicon-generator.org/). Via the site,  you just need to upload a picture, then it will gernerate a pakege of pitures of different sizes, and also a puntch of codes that will be added to the header of HTML  file.

For the site template I used,  I need to replace all the images in `/assets/images/favicon` file and change the favicon codes in `/_includes/favicon.html` file to the those generated in the site. Finnally need to change all the `href`  atrributes to the right path, the images are not under root directory, so you need to add `/assets/images/favicon` before the path.

![href-path](/assets/images/blog-image/href-path.jpg)

### Change the style of my profile photo

I was going to change it and changed, but I found the style of the prime is quite good, so I keep it. But I still want to record how to change it, it would be helpful if one day I still need to change the styles of the site. You can find and edit the main css code in the file  `/assets/styles/main.css`, but before edict it, you should know the selector of the one you'd like to change, the selector is the key, through the key, you can find it's styles. To get the selector, you need the Chrome browser's help. Let's see how to get the selector of my site's profile photo:

1. Open my site in Chrome, and right click the profile photo, then click Inspect.

   ![click-inspect](/assets/images/blog-image/click-inspect.jpg)

2. You can see the selector under the 'style' tab.

   ![selector](/assets/images/blog-image/selector.jpg)

3. You can [change the elements' style in Chrome](https://developers.google.com/web/tools/chrome-devtools/css#declarations) and see the new effect on your site directly, but it only for test, it will not change the style of your site. If you want the new style to be applied in your site, you should back to the file `/assets/styles/main.css` to change the style. 
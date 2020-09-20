## New updates for my blog

### Connect a custom domain

From several days ago, I can't reach githu.io pages, like wkeiss.github.io. And I found if there is a domain connect to github page, then we can visit it. So I decided to buy and connect a domain to my website.

I choose to buy a domain in Aliyun, since compared to registars like namecheap, Gandi, and others in overseas, it's more possibly to buy a cheaper domain in china registars. 

Later you should  follow the help doc to connect domain to your github page: [Managing a custom domain for your GitHub Pages site - GitHub Docs](https://docs.github.com/en/github/working-with-github-pages/managing-a-custom-domain-for-your-github-pages-site). 

Finally, I need to update the site url to the new one after the site can be visit via domain in [_config.yml](https://github.com/wkeiss/wkeiss.github.io/blob/master/_config.yml) file.

### Add Disqus 

I hope people can comment my blog, though I think almost nobody visits my site, but maybe  someday there will be someone want to leave a comment, so I decided to add disuqs to my site.

First you need to add your site your Disqus account, if you don't have a Disqus account yet, you need to register one firstly. 

If you like me use the Jekelly theme to build your site, you don't need to install disqus into your site. But you should add your site to your disqus account to get your site's short name start from here:https://disqus.com/admin/create/. Then you will head to a select plan page, you can don't buy a plan now, just skip to step 3 configure Disqus buy click "Configure Disqus", and input the inqured info, click 'Complete Setup' in the bottom right corner.

### ![configure-disqus](/assets/images/blog-image/configure-disqus.jpg)

Head to the https://disqus.com/admin/settings/general/  and click the site you just added, then you can see your site's short name.

![click-the-site-just-added](/assets/images/blog-image/click-the-site-just-added.jpg)

![short-name](/assets/images/blog-image/short-name.jpg)

Finally, add the short name to the  [_config.yml](https://github.com/wkeiss/wkeiss.github.io/blob/master/_config.yml) file, all setup.

### Change the favicon 

Before I did it, I found the relative file and code in my githubpage resposity. I thought it was quite troblesome to change the favicon, since I need to change the picture I choose as favicon to about 7 sizes, and then I have to change the path in 'href' attribute. or I need to named the new photoes like these show in the files, then I don't need to change to path. All in all, no matter how, they are troublesome! 

When I tried to find an easy way to change my favicon, I found [a site to generate favicon quite simplily](https://www.favicon-generator.org/). you opload an picture, then it will gernerate a pakege of pitures of different sizes, and also a puntch of codes that will be added to header.

Then I need to replace all the images in /assets/images/favicon file and change the favicon codes in /_includes/favicon.html file to the those generated in the site. Finnally need to change the href to the right path, the images are not under root directory, so you need to add /assets/images/favicon before the path.

![href-path](/assets/images/blog-image/href-path.jpg)
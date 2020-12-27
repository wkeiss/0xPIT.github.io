---
title: "如何在 Heroku 部署 Django 项目"
layout: post
date: 2020-12-01
tag:
- "2020"
- "blog"
- "growth"
- ”work"
blog: true
---

我做了 [孤岛 ](https://github.com/wkeiss/lonelyisland)这个网站应用，网站的用户只有我自己一个人，别人可以看见我发布的碎片的简单的想法。这个项目对于Django 的老手来说，简单得不能再简单了，但是我做出来可是用了好大劲呢！也许是经常使用  [Github Page](https://pages.github.com/)来发布博客文章，所以想着发布自己的网站应用也应该是一样简单的事情。但是我的整个发布网站的过程一度让我崩溃。

博客这类只有 HTML， CSS 和 JavaScript 这三种运行在浏览器端的代码的网站属于静态网站，发布基本上就是上传代码到云服务器就可以。然后根据相应的域名就可以直接访问。比如我发现的这个可以免费发布一个静态网站的平台：  https://neocities.org ，还有我现在博客正在使用的 [Github Page](https://pages.github.com/), 就可以帮你很轻松发布自己的网站。而网站应用呢，除了有静态的网页模板外，还需要与数据库交互，比如我的孤岛这一个简单发布自己碎片想法的应用，需要将数据写入数据库，然后服务器调用需要的 post 将它们集成一个网页再传回用户端，在浏览器中展示。所以发布网站应用，让自己的代码能够按照自己的预期在相应服务端平台运行起来，要多做些工作。

Heroku 发布 Django 应用总体来说是很方便的，几乎也用 Github Page 来发布博客一样，将代码传上去就可以了。在部署网站应用之前，我的 Django 应用已经能在本地运行了。于是接下来的部署我是参照 [Django Tutorial Part 11: Deploying Django to production - Learn web development - MDN](https://developer.mozilla.org/en-US/docs/Learn/Server-side/Django/Deployment) 这篇教程来完成的。为什么不看官方文档呢，因为官方文档没有 MDN 这篇这么详细，对新手如此友好，但是遇到问题或者不明白的地方，会结合官方文档来查证信息。

首先先按照 MDN 的教程准备好相应的文件，比如 **requirement.txt**, **runtime.txt**, **Procfile** 等。需要注意 **Procfile** 这个文件的内容：`web: gunicorn locallibrary.wsgi --log-file -` .你应该将里面的 locallibrary 更改你的项目名，也就是这个项目在 github 的仓库名， 我的是 lonelyisland, 所以我的 **Procfile** 这个文件的内容写入的是 `web: gunicorn lonelyisland.wsgi --log-file -` 

接着就真正开始部署了。在一开始的时候我就遇到一个困难：无法登陆 Heroku。在终端输入 > heroku create ， 点击任何一个非 'q' 的键后会在打开一个登陆页面。我的会一直报错 invalid request， 或者请求因服务器长时间不响应失败，需要检查代理或防火墙的。经验觉得可能是需要翻墙才能登录。想看看国内的 Heroku 用户有没有遇到登陆不上的问题，于是使用国内搜索引擎搜索相关的关键词，发现了[一个解决办法](https://blog.csdn.net/qq_42951560/article/details/109717160)：

>  在终端输入 `heroku login -i` ，使用 Heroku 用户邮箱和密码登录。

接着你可以按照 [Django Tutorial Part 11: Deploying Django to production - Learn web development - MDN](https://developer.mozilla.org/en-US/docs/Learn/Server-side/Django/Deployment) 这篇教程来继续后终端完成部署。或者你也可以在 Heroku 官网完成部署。我是后面发现部署完成后，发现不管怎样都需要在终端操作才寻找到上面的登录方式的，所以在这之前，我是先在 Heroku 上完成部署。

首先注册之后，在 https://dashboard.heroku.com 点击 create a app, 然后就按照提示授权 Github 账号和选择部署项目的仓库。然后选择自动部署，这样每一次你 Git Push 到仓库的时候， Heroku 都会自动部署你的网站。让我崩溃的就是这个部署的过程，报错的 Logs 密密麻麻，眼花缭乱心也乱。来~ 感受一下密密麻麻 ↓ ：）

> ```python
> -----> $ python manage.py collectstatic --noinput
>        Traceback (most recent call last):
>          File "/app/.heroku/python/lib/python3.7/site-packages/django/core/management/__init__.py", line 224, in fetch_command
>            app_name = commands[subcommand]
>        KeyError: 'collectstatic'
>        During handling of the above exception, another exception occurred:
>        Traceback (most recent call last):
>          File "manage.py", line 22, in <module>
>            main()
>          File "manage.py", line 18, in main
>            execute_from_command_line(sys.argv)
>          File "/app/.heroku/python/lib/python3.7/site-packages/django/core/management/__init__.py", line 401, in execute_from_command_line
>            utility.execute()
>          File "/app/.heroku/python/lib/python3.7/site-packages/django/core/management/__init__.py", line 395, in execute
>            self.fetch_command(subcommand).run_from_argv(self.argv)
>          File "/app/.heroku/python/lib/python3.7/site-packages/django/core/management/__init__.py", line 231, in fetch_command
>            settings.INSTALLED_APPS
>          File "/app/.heroku/python/lib/python3.7/site-packages/django/conf/__init__.py", line 83, in __getattr__
>            self._setup(name)
>          File "/app/.heroku/python/lib/python3.7/site-packages/django/conf/__init__.py", line 70, in _setup
>            self._wrapped = Settings(settings_module)
>          File "/app/.heroku/python/lib/python3.7/site-packages/django/conf/__init__.py", line 196, in __init__
>            raise ImproperlyConfigured("The SECRET_KEY setting must not be empty.")
>        django.core.exceptions.ImproperlyConfigured: The SECRET_KEY setting must not be empty.
>  !     Error while running '$ python manage.py collectstatic --noinput'.
>        See traceback above for details.
>        You may need to update application code to resolve this error.
>        Or, you can disable collectstatic for this application:
>           $ heroku config:set DISABLE_COLLECTSTATIC=1
>        https://devcenter.heroku.com/articles/django-assets
>  !     Push rejected, failed to compile Python app.
>  !     Push failed
> ```

报错本身并不会让人沮丧或烦躁，因为即便自己的编程时间不长，我还是清楚报错的家常便饭，并且报错是给予很反馈，让你知道哪里可以修改来帮助你实现你所预期的效果，在安装多 Package 或者 Library 后，会因为他们的开发者会提供尽可能的准确的报错定位和原因而内心感激不已，因为他们节约了我们的时间。让人烦躁或沮丧的是我们对于如果解决报错的问题一无所知。

我知道上面提到两个问题，一个是我的 `SECRET_KEY` 没有设置，另外一个是 `python manage.py collectstatic --noinput` 这个命令不能正常运行。通过搜索 StackOverflow, 看到后面这个 collectstatic 的任务就是需要更改 static file 的地址，我更改了部署还是一样的报错。搞来搞去，差不多  3 个小时。于是将报错信息还有 `setting.py` 这个文件的代码放到 StackOverflow 寻求帮助。结果不久就有人回答我的问题了。根据某一个回答，知道了可以在我的 Heroku Project 的 Setting > Config Vars 设置我的 `SECRET_KEY`。 设置好后再手动部署，发现没有的 `SECRET_KEY` 的报错信息。在 StackOverflow 上询问问题，即便没有人真正解决你的问题，但是别人热心的帮助会让我很有动力继续去探索寻求解决办法。我看到 `python manage.py collectstatic --noinput`  是一个 Django 的命令，于是我试着在本地运行，报错说我的 static 的路径错了，根据相应的路径并不能找到 static  文件。于是我根据报错回到 setting.py 文件重新修改寻找 static 文件的路径到实际上我放 static 文件的地址，再运行代码后我就可以正常运行 `python manage.py collectstatic --noinput`  了，并且它会生成一个 `staticfiles` 文件。我将修改 Git Push 到仓库，自动部署成功了。

只是打开项目的网页，还是有报错信息，是我们在本地开发的时候熟悉的 Django 的报错页面。根据具体的报错信息，在 `setting.py ` 文件给 `ALLOWED_HOSTS` 添加 `lonelyislandcindy.herokuapp.com`  这个域名，这样网站才可以在这个域名下显示。然后有一个问题：

> ProgrammingError at /relation "posts_post" does not exist LINE 1: ..."posts_post"."body", "posts_post"."pub_date" FROM "posts_pos...

它指向的是我的 template 中使用的  for 循环来访问所有数据库中保存的 post 数据这部分的代码。经过搜索，发现是自己没有在本地终端输入 `heroku run python manage.py migrate --app lonelyislandcindy`  来使数据库应用于我们的应用。因为我不是在终端部署我的网站应用的，所有当我使用 heroku 的命令的时候，后面在添加 `--app appNameOnHeroku` 来指定是对哪一个应用执行命令。最后发现就可以正常访问网站了。发现之前添加的  Post 都没有了，使用之前创建的一个用户账号也不能登录了，这是因为本地开发的时候我们使用的是 SQLite 来作为数据库，而 Heroku 不支持使用 SQLite, 它免费提供来作为数据库，我们免费的账号使用的就是这个数据库，数据库改变了，所以就没有了原来的信息。需要新建用户我们先需要新建一个超级用户来登录后台，新建超级用户是在终端输入 `heroku run python manage.py createsuperuser --app appNameOnHeroku` 。然后通过在 App 网页地址后加上 `/admin` 来访问管理页面，接下来你就是你熟悉的 Django 管理页面啦，你应该知道该怎么做。

Heroku 的应用也支持免费添加自己的域名，只是需要添加信用卡信息来做验证 Heroku 账户。具体你可以参考他们的官方文档 [Custom Domain Names for Apps -Heroku Dev Center](https://devcenter.heroku.com/articles/custom-domains).

整个部署的过程，因为终端登录不上 Heroku 我以为我用不了 Heroku, 我转而去使用 Pythonanywhere, 尝试过 ASW， 腾讯云，最终都被让我束手无策的报错信息劝退了。可是我想着一定要部署出来，而且考虑自己今后会一直使用这个应用，就想着很久，觉得 Heroku 比较适合我，而且它有 MDN 的文档帮助我，再加上遇到问题的时候去搜索会发现 Heroku 会更容易搜到相关的问题，部署起来也是相对来说对新手比较友好的，我就决定就 Heroku 了，不管遇到什么问题我都要用它来完成部署。事实证明，代码的问题也是心力的问题，如果心力足了，不管中间遇到多少崩溃的报错，最终都会解决的。
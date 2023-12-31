---
title:       "Hugo + Github Pages + Github Actions Blog deployment plan"
subtitle:    "Blog Set Up"
description: "This article introduces the use of Hugo as the blog source code, Github Page as the deployment solution and the use of Github Action to configure CI/CD"
date:        2023-11-02T12:00:00
author: UNKNOWN SPACE
# image:       ""
tags:        ["Hugo"]
categories:  ["post"]
URL:         "/2023/11/03/HugoSetUp/"
# draft:       false
---

<!-- >记忆里自从2021年开始就计划着要弄博客，结果一直想法大于行动，一直拖到了现在才弄好，老拖延症了，这里分享一下我创建博客的过程以便大家参考与复制 -->
>In my memory, I have been planning to start a blog since 2021, but the idea has always been greater than the action. It has been delayed until now. I am an old procrastinator... I will share my process of creating a blog for your reference and copying.

<!--more-->
<!-- ## Hugo的安装与配置 -->
## Hugo Installation and Configuration
<!-- 要在windows上使用Hugo， 首先要安装**Git**，**Go**，以及**Dart Sass**，虽然不是所有情况下都需要，但是这三种语言和工具是最常见的。这里可以前往对应的官网进行安装，此处就不对安装过多赘述了。 -->
To use Hugo on Windows, you must first install **Git**, **Go**, and **Dart Sass**. Although not required in all cases, these three languages and tools are the most common. Here you can go to the corresponding official website to install it. I won’t go into too much detail about the installation here.

<!-- 安装链接： -->
Installation Link:  
[Git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git)  
[Go](https://go.dev/doc/install)  
[Dart Sass](https://gohugo.io/hugo-pipes/transpile-sass-to-css/#dart-sass)

<!-- 完成安装之后，我们需要在hugo的theme里面选择一个作为主题，我这里使用的是[Clean White](https://themes.gohugo.io/themes/hugo-theme-cleanwhite/)主题。选好之后我们使用hugo命令创建新的站点 -->
After completing the installation, we need to choose a theme from hugo's theme. I am using the [Clean White](https://themes.gohugo.io/themes/hugo-theme-cleanwhite/) theme. After selecting, we use the hugo command to create a new site.
```bash
hugo new site
```
<!-- 随后进入主目录，将选定的主题clone到theme路径下 -->
Then enter the home directory and clone the selected theme to the theme path.
```bash
cd <your_folder_name>
cd theme
git clone https://github.com/zhaohuabing/hugo-theme-cleanwhite.git # your theme
```

<!-- 在把theme配置好之后，最简单的开始配置的方式是将theme中的样例站点复制到hugo源路径来，这样我们可以通过观察配置文件和站点具体效果的映射来修改相对应的代码。使用以下命令来进行复制。 -->
After configuring the theme, the easiest way to start the configuration is to copy the sample site in the theme to the hugo source path, so that we can modify the corresponding code by observing the mapping between the configuration file and the specific effects of the site. Use the following command to copy.
```bash
cp -r hugo-theme-cleanwhite/exampleSite/** ../
```
<!-- 这时我们可以测试我们的样例站点是否配置成功，使用以下命令来在`localhost`打开 -->
At this time we can test whether our sample site is configured successfully and use the following command to open it on `localhost`
```bash
hugo server
```
<!-- 运行过后进入`http://localhost:1313/`即可。要修改博客网页中的元素，我们需要修改hugo.toml文件，这里可以查看选择的theme的文档来学习如何配置，这里附上Clean White的git仓库地址 https://github.com/zhaohuabing/hugo-theme-cleanwhite, 修改过后保存文件，在`http://localhost:1313/`就能看到我们做出的更改。

hugo的博客文章都存储在content路径下，其中content下的文件夹代表我们的具体分页，打开一个文件夹后我们可以看到该文件夹下面的所有博客文件。每一篇博客开头我们需要有该博客的相关信息，这里拿出一个作为示例（此为Clean White的配置信息，具体可以在不同theme的exampleSite进行查看）。 -->
After running, enter `http://localhost:1313/`. To modify the elements in the blog web page, we need to modify the hugo.toml file. Here you can view the documentation of the selected theme to learn how to configure it. Here is the Clean White git warehouse address https://github.com/zhaohuabing/hugo- theme-cleanwhite, save the file after modification, and you can see the changes we made at `http://localhost:1313/`.

Hugo's blog posts are stored under the content path, where the folder under content represents our specific paging. After opening a folder, we can see all the blog files under the folder. At the beginning of each blog, we need to have relevant information about the blog. Here is one as an example (this is the configuration information of Clean White, which can be viewed in the exampleSite of different themes).
<!-- ---
title:       "Hugo + Github Page + Github Action博客部署方案"
subtitle:    "Blog Set Up"
description: "本文介绍使用Hugo作为博客源码，Github Page作为部署方案以及利用Github Action配置CI/CD"
date:        2023-11-03
author:      "不知所云集"
image:       ""
tags:
    - "Hugo"
categories:  ["post"]
URL:        "/2023/11/03/HugoSetUp/"
draft: true
--- -->
```bash
---
title:       "Hugo + Github Pages + Github Actions Blog deployment plan"
subtitle:    "Blog Set Up"
description: "This article introduces the use of Hugo as the blog source code, Github Page as the deployment solution and the use of Github   Action to configure CI/CD"
date:        2023-11-02
author:      "UNKNOWN SPACE"
image:       ""
tags:        ["Hugo"]
categories:  ["post"]
URL:         "/2023/11/03/HugoSetUp/"
draft:       false
---
```
<!-- 这里需要注意，如果`draft: true`存在于配置项的话那么文章是不会被看到的，需要删除这一行文章才能出现在界面上。完成配置之后我们要在下面使用markdown语法编写正文，这里不对markdown做过多赘述。

如果要创建新的博客文章，运行以下命令 -->
It should be noted here that if `draft: true` exists in the configuration item, the article will not be seen. You need to delete this line before the article can appear on the interface. After completing the configuration, we will use markdown syntax to write the text below. I will not go into details about markdown here.

If you want to create a new blog post, run the following command
```bash
hugo new post/your_blog_name.md
```
<!-- 这里的`post`代表content路径下的文件夹名字，`/`后面则是要创建的文件名。 -->
Here `post` represents the folder name under the content path, and `/` is followed by the name of the file to be created.

<!-- ## Github Pages部署 -->
## Github Pages Deployment
<!-- 在完成我们的配置以及文章调整后，我们可以着手部署我们的博客。这里我们将使用Github pages来进行部署。首先先在Github创建一个仓库，仓库名为`<username>.github.io`，这里要把`<username>`替换为你的Github用户名，注意仓库的名字必须是这个形式，否则无法生效。

把该仓库克隆到本地 -->
After completing our configuration and article adjustments, we can start deploying our blog. Here we will use Github pages for deployment. First, create a warehouse on Github. The warehouse name is `<username>.github.io`. Here you need to replace `<username>` with your Github username. Note that the name of the warehouse must be in this form, otherwise it will not take effect.

Clone the repository locally
```bash
git clone https://github.com/<username>/<username>.github.io.git
```
<!-- 现在我们可以对hugo源文件进行打包操作，方式很简单，前往我们Hugo站点的根路径，运行以下命令 -->
Now we can package the hugo source files. The method is very simple. Go to the root path of our Hugo site and run the following command
```bash
hugo
```
<!-- 我们可以看到有一个./public文件夹被创建，这个文件夹就是我们需要的用于部署的静态页面，将此文件夹复制到我们克隆的Github pages文件夹下。

复制过后将此文件夹的内容push到Github仓库中 -->
We can see that a ./public folder has been created. This folder is the static page we need for deployment. Copy this folder to the Github pages folder we cloned.

After copying, push the contents of this folder to the Github repository.
```bash
git add --all
git commit -m "Initial Commit"
git push
```
<!-- 等待自动部署完毕，就可以在浏览器输入`https://<username>.github.io`来查看博客。

Congratulations！现在你拥有了一个属于你自己的博客了。 -->
After the automatic deployment is completed, you can enter `https://<username>.github.io` in the browser to view the blog.

Congratulations! Now you have a blog of your own.

<!-- >注：这里我在部署的时候出现了CSS不显示的问题，原因是因为前面配置的.toml文件出现了错误，如果你遇到了同样的问题，建议修复流程如下  
>1. 检查baseurl是否正确，形式应该为`baseURL = "https://<username>.github.io"`
>2. 在开头部分加入true的那个 -->
>Note: Here I encountered the problem of CSS not being displayed during deployment. The reason is that there was an error in the .toml file configured earlier. If you encounter the same problem, the recommended repair process is as follows
>1. Check whether the baseurl is correct, the form should be `baseURL = "https://<username>.github.io"`
>2. Add the true one at the beginning

<!-- ## 使用Github Actions配置CI/CD -->
## Github Actions CI/CD Configurations

<!-- 尽管现在我们已经可以编写并且修改博客，但是现在我们修改的流程十分复杂，每次在更新过后都需要构建hugo，复制public文件夹到Github pages再进行上传。为了专注于写作，我们可以通过配置CI/CD来简化该流程，这里我们选择使用Github Action来配置。

首先我们需要配置我们的 `Personal access token` ，这是一种在不需要密码验证的情况下调用API进行程序化操作的方式。这里需要在Github的右侧边栏内点击Setting（点击头像弹出来的侧边栏，注意不是仓库内的Setting），在Setting中点击 `Developer Setting`。 -->
Although we can now write and modify blogs, our modification process is very complicated now. Every time we update, we need to build hugo, copy the public folder to Github pages, and then upload it. In order to focus on writing, we can simplify the process by configuring CI/CD. Here we choose to use Github Action to configure.

First we need to configure our `Personal access token`, which is a way to call the API for programmatic operations without requiring password verification. Here you need to click Setting in the right sidebar of Github (click the sidebar that pops up on the avatar, note that it is not Setting in the warehouse), and click `Developer Setting` in Setting.

![](/img/hugo_blog/token1.png)

<!-- 这里我们选择 `Classic Token` 就可以了，点击右上角的 `Generate new token` -->
Here we just select `Classic Token` and click `Generate new token` in the upper right corner

![](/img/hugo_blog/personal_access_token.png)

<!-- Note随便填，在下面的 `Select Scopes` 中选择 `workflow` -->
 Fill in whatever you want with Note, select `workflow` in `Select Scopes` below

![](/img/hugo_blog/token2.png)

<!-- 点击Generate Token之后，注意及时复制生成的Token，如果退出了界面但是还没复制那就只能重新生成一个。接下来我们前往Hugo源文件的Github项目下，进入Setting，选择Secrets，在Actions中选择 `New repository secret`。 -->
After clicking Generate Token, pay attention to copy the generated Token in time. If you exit the interface but have not copied it, you can only regenerate one. Next, we go to the Github project of the Hugo source file, enter Settings, select Secrets, and select `New repository secret` in Actions.

![](/img/hugo_blog/token3.png)

<!-- 在Name中填写PERSONAL_TOKEN(在.yml文件中设置的值)，然后在Secret中填写我们复制的Token，点击`Add secret`完成Token的生成。 -->
Fill in PERSONAL_TOKEN (the value set in the .yml file) in Name, then fill in the Token we copied in Secret, and click `Add secret` to complete the Token generation.

![](/img/hugo_blog/token4.png)

<!-- 完成Token的生成后，我们要进行Github Actions的配置。先将我们的hugo根目录放到一个github仓库里面，并在仓库中添加`.github/workflows`路径，在这个路径下创建一个`.yml`文件，在这里我们需要编写CI/CD的相关信息以及具体流程。我们需要Github来帮我们完成的事项主要有

1. 在读取到push更改后自动构建hugo
2. 在构建hugo后自动将public文件夹下的内容上传到Github pages的文件夹
3. 在Github pages的仓库中push最新的更改从而自动调用Github pages的部署

这里我的`.yml`文件如下： -->
After completing the generation of Token, we need to configure Github Actions. First put our hugo root directory into a github warehouse, add the `.github/workflows` path in the warehouse, and create a `.yml` file under this path. Here we need to write CI/CD related information and specific procedures. The main things we need Github to help us complete are:

1. Automatically build hugo after reading push changes
2. After building hugo, automatically upload the contents of the public folder to the Github pages folder.
3. Push the latest changes in the Github pages repository to automatically call the deployment of Github pages

Here my `.yml` file is as follows:

<!-- name: unknown_space # 替换为你的Hugo源文件仓库名

on:
  push:
    branches:
      - main # 分支名称，这里我的是main

jobs:
  build-deploy:
    runs-on: ubuntu-latest
    steps:
      - name: Check out source
        uses: actions/checkout@v2

      - name: Setup Hugo
        uses: peaceiris/actions-hugo@v2
        with:
          hugo-version: '0.119.0' # 替换为你的hugo版本，可以使用hugo version在命令行查看
          extended: true #是否为extended版本

      - name: Build
        run: hugo

      - name: Deploy
        uses: peaceiris/actions-gh-pages@v3
        with:
          personal_token: ${{ secrets.PERSONAL_TOKEN }} # 另外还支持 deploy_token 和 github_token
          external_repository: <username>/<username>.github.io # 修改为你的username
          publish_dir: ./public
          publish_branch: main # 目标仓库的分支名称 -->
```bash
name: unknown_space # Replace with the name of your Hugo source file repository

on:
  push:
    branches:
      - main # Branch name，here mine is main

jobs:
  build-deploy:
    runs-on: ubuntu-latest
    steps:
      - name: Check out source
        uses: actions/checkout@v2

      - name: Setup Hugo
        uses: peaceiris/actions-hugo@v2
        with:
          hugo-version: '0.119.0' # replace to your hugo version，use hugo version to check at command line
          extended: true # extended hugo version or not (chosed while installation)

      - name: Build
        run: hugo

      - name: Deploy
        uses: peaceiris/actions-gh-pages@v3
        with:
          personal_token: ${{ secrets.PERSONAL_TOKEN }} # deploy token and github token are also supported
          external_repository: <username>/<username>.github.io # change to your username
          publish_dir: ./public
          publish_branch: main # target branch name
```

<!-- 完成之后我们可以上传进行测试，如果在Actions中看到build通过，等待一会之后查看我们的站点是否应用了更改。如果更改那就大功告成~ 至此我们的配置就结束了。

未完待续~（会更新如何在浏览器可以被搜索到的教程） -->
After completion, we can upload it for testing. If we see that the build passed in Actions, wait for a while and see if the changes have been applied to our site. If you change it, you're done~ At this point, our configuration is over.

To be continued~ (The tutorial on how to be searchable in the browser will be updated)
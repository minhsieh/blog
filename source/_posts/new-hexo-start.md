title: Hexo部落格框架 我來了！
date: 2018-01-10 14:18:41
tags: [hexo, nodejs, npm, blog]
categories: []
---
安裝Hexo
---------
我的環境是AWS EC2上的Ubuntu主機，首先要先安裝Nodejs和NPM

```
npm install hexo-cli -g
```

這時候你就可以使用*hexo*這個命令去執行相關的動作。

<!--more-->

在你要開目錄的位置，使用 *hexo init* 建立一個新的專案

```
cd /your-path/
hexo init blog
```

這時候hexo會開始跑一些npm的前置，當看到
```
INFO  Start blogging with Hexo!
```

就代表成功了。

再來安裝一些需要的npm套件和環境
```
cd blog
npm install
```

就完成了，這時候可以啟動伺服器來看看

```
hexo s -p 8080
```

這時候連到你的主機網頁看看，就會看到一個全新的Hexo部落格在對你招手啦！
http://localhost:8080/

設定Hexo
---------

在你的hexo目錄底下可以找到 *_config.yml* 這個設定檔，你可以透過編輯這個設定檔來修改成你要的配置。


新增文章
--------
用Hexo新增文章，個人不確定算是好用還是不好用，因為剛接觸而已，但在這裡它是使用*Markdown*語法作為編輯格式，在寫完文章以後存成.md的檔案，然後可以用 *hexo generate* 產生出靜態檔。

新增文章的指令

```
hexo new [layout] 你的文章標題
```


其中layout有分成三種： *post(文章)* , *draft(垃圾桶)* , *page(頁面)* ，也分別會產生在 *source/_posts* 等對應的資料夾底下。

前面有提到，產生出來的檔案會是 *.md* 檔格式，可以參考[Markdown TW](http://markdown.tw/)的文件來撰寫。

產生靜態檔案
----------

編輯完文章以後，可以執行下面命令

```
hexo generate
```

hexo會將在source裡面的md檔，轉成靜態的html5格式並放置在 *public* ,而 *public* 這個資料夾其實就是獨立一個小小的靜態網站，你甚至可以把整個資料夾複製後拿去任何地方部署，也可以使用hexo的部署指令，進行一鍵部署。

```
hexo deploy
```


更換主題
---------
Hexo當時還有一個非常吸引我的地方，那就是他的佈景主題超多，而且全部都是開源的，有為數眾多的工程師使用Hexo作為自己的部落格框架，理所當然也有很多人貢獻自己的佈景主題在Github上，你可以到Hexo的官方網站[查看](https://hexo.io/themes/)，找出你想要的佈景主題。

找到以後，將該Repository clone到自己的hexo目錄下的 *themes* 目錄。這邊我找到的是[pinggod/hexo-theme-apollo](https://github.com/pinggod/hexo-theme-apollo)

```
cd /var/www/blog
git clone https://github.com/pinggod/hexo-theme-apollo.git themes/apollo[佈景名稱，此處自定]
```

然後到 *_config.yml* 裡面，將theme更改成剛才你在 *themes* 目錄裡面命名的那個主題資料夾

```
theme: apollo
```

之後重新 *hexo generate* 後，就能看到新的主題套用在你的Hexo上啦

那今天的紀錄就到這裡，之後如果還有其他關於Hexo的操作，在上來這邊跟大家分享。

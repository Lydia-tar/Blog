# Sphinx




生成新网页:.\make clean + .\make html

更新目录：在source/index.rst 中增加


``` 
两个点..+空格+后面的文本，代表注释（网页上不显示）
等号线====+上一行的文本，代表一级标题
.. toctree::声明的一个树状结构（Table of Content Tree）
:maxdepth: 2 表示页面的级数最多显示两级
:caption: Contents: 用于指定标题文本（可以不要）
最下面的3行是索引和搜索链接（可以先不用管）
```


上传代码到github
在git bash中：
```
rm -rf docs/**
touch docs/.nojekyll
cp -r build/html/* docs/


git add *
git commit -m "add detail"
git push
```
![imagefilename](/_static/git.png)


## 搭建过程

##预览
sphinx-autobuild source build/html 

##插入图片
把图片放入source/static
```
![imagefilename](/_static/.....)
```

markdown:
https://www.markdownguide.org/basic-syntax/

##定制
https://sphinx-themes.org/sample-sites/mozilla-sphinx-theme/kitchen-sink/
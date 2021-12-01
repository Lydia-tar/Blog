# Sphinx


## 本地实时预览
```
sphinx-autobuild source build/html 
```

## 修改本地仓库，生成新网页:
```
.\make clean 
.\make html
```

## 修改远程仓库，上传代码到*github*
在**git bash**中：
```
rm -rf docs/**
touch docs/.nojekyll
cp -r build/html/* docs/


git add *
git commit -m "add detail"
git push
```
![imagefilename](/_static/git.png)


---

## markdown:

[https://www.markdownguide.org/basic-syntax/](https://www.markdownguide.org/basic-syntax/)

[中文版](https://www.markdown.xyz/basic-syntax/#paragraphs)


1. 插入图片

    把图片放入source/static
```
![imagefilename](/_static/.....)
```

2. 块引用
>在段落前加>
>
>- 要换行，也要输入>
>>- 嵌套块就多输入>>
>>> - 要嵌套多少层就多输入几个>

3. 代码块

    单对反引号是字`code`

4. 分割线---

---

## 定制

[https://bashtage.github.io/sphinx-material/](https://bashtage.github.io/sphinx-material/)

icon:
[https://fonts.google.com/icons](https://fonts.google.com/icons)


## 搭建sphinx+github过程
[https://www.bilibili.com/video/BV1EE411N7Bi?p=1]（https://www.bilibili.com/video/BV1EE411N7Bi?p=1）

1. 安装python
2. 安装sphinx 
```
pip install sphinx
```
创建新的文件夹，cmd进入当前文件夹，输入：
```
sphinx-quickstart
```

此时build 文件夹下面是空的，执行 make html，可以打开index.html

实时查看不按照教程里的live-server,而是直接使用sphinx-autobuild

```
#install
python -m pip install sphinx-autobuild

#usage
sphinx-autobuild source build/html
```

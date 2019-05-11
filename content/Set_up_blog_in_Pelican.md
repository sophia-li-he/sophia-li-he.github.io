Title: Set up a blog in Pelican
Date: 2019-05-10 10:20
Category: Python

# Set up a blog in Pelican
```bash
source activate pyspark_env
pip install pelican markdown
```
Create a new github repo with repo name as sophia-li-he.github.io
Change directory to the folder where you want to save your blog
```bash
$ git clone https://github.com/sophia-li-he/sophia-li-he.github.io.git
```
Change to the new directory
```bash
cd sophia-li-he.github.io
```

Use Pelican quickstart
```bash
pelican-quickstart
```

Answer below questions
> Where do you want to create your new web site? [.] 
> What will be the title of this web site? Sophia He's Data Blog
> Who will be the author of this web site? Sophia He
> What will be the default language of this web site? [en] 
> Do you want to specify a URL prefix? e.g., https://example.com   (Y/n) Y
> https://sophia-li-he.github.io
> Do you want to enable article pagination? (Y/n) n
> What is your time zone? [Europe/Paris] America/New_York
> Do you want to generate a tasks.py/Makefile to automate generation and publishing? (Y/n) Y
> Do you want to upload your website using FTP? (y/N) N
> Do you want to upload your website using SSH? (y/N) N
> Do you want to upload your website using Dropbox? (y/N) N
> Do you want to upload your website using S3? (y/N) N
> Do you want to upload your website using Rackspace Cloud Files? (y/N) N
> Do you want to upload your website using GitHub Pages? (y/N) y
> Is this your personal page (username.github.io)? (y/N) y
Done. Your new project is available at /Users/sophiahe/Sophia/700_Tech/780_data_blog/sophia-li-he.github.io

Generate content of the blog
```
pelican content
```

Preview the blog at http://localhost:8000/
```
pelican -l
```

Push your changes to github
```bash
$ git add -A && git commit -a -m 'first commit' && git push --all
```
```bash
#make publish
make github
```
The blog can be viewed here: https://sophia-li-he.github.io

**Reference:**
1. https://rsip22.github.io/blog/create-a-blog-with-pelican-and-github-pages.html
2. https://fedoramagazine.org/make-github-pages-blog-with-pelican/
3. https://opensource.com/article/19/1/getting-started-pelican
4. http://docs.getpelican.com/en/stable/publish.html
5. https://blog.udacity.com/2016/02/how-to-build-a-data-analysis-portfolio-that-will-get-you-hired.html
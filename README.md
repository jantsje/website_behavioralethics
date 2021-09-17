# Website behavioralethics.org

Here is a readme to explain how to update our lab website www.behavioralethics.org. 
Expect clear instructions but no passwords. 

The website is built with Wowchemy (formerly Hugo Academic) in [R Bookdown](https://bookdown.org/yihui/blogdown/). 

## How to adjust text / pictures / links
Most information can be found in the [Wowchemy docs](https://wowchemy.com/docs/). 
Most entries consist of text (you can change that in `_index.md`) 
and a picture (`featured.jpg` or `avatar.jpg`). 
We have the following headers:
- Projects (`content/project`)
- People (`content/authors`)
- News & Media (`content/post`)
- Publications (`content/publications`)
- Contact (`content/home/contact`)

To change the main text / image, go to `content/authors/admin`.
To change things in the menu, go to `config/_default/menus`.

## How to add publications
Two options: manually (I often copy an existing publication and change the text)
or with bibtex. If you want to add many publications, you can import them through bibtex. 
You need one bibtex file with all the new entries. 

I use [Mendeley](https://www.mendeley.com/download-desktop-new/) to do this. 
If you make a new **group** (!! not a **folder**) with a reasonable name, such as 
`new_publications_website`, you can add all new publications there. 
In Mendeley, go to `Tools > Options > BibTeX` and enable `Create one BibTex file per group`. 
Check where this is exported, and copy the `new_publications_website.bib` 
file to the root of the Blogdown folder. 

In R-studio, run `academic import 
--bibtex new_publications_website.bib`. If that did not work, 
you first need to install the academic plugin. 
Run `pip3 install -U academic` or check 
[this page](https://wowchemy.com/docs/content/publications/). 
The academic plugin will now import your new publications. 
You might need to adjust some things (such as `url_pdf` 
which may still point to a local copy) 
and whether you want to link the publication to a `project`. 

## How to update and push to the server
In R-studio, I have the BLOGDOWN plugin. After making changes locally, 
run `blogdown:::serve_site()` to check in your local browser if you like the changes. 
Then, run `blogdown:::build_site()` to build the site. 
This will update the contents of the **public** folder, 
which is the folder you need to push to the server. 
If the `build_site` command does not work, you probably have an unclosed parenthesis. 
Alternatively, you need to update Hugo. 
Run `hugo mod clean` at the root of your local project. 

For pushing to the server, connect with FTP (I use [FileZilla](https://filezilla-project.org/)). 
Navigate to `domains/behavioralethics.org/public_html/` and upload/replace your changes from the local `public` folder. 
You might get a message `target file already exists` and you can tick `overwrite if source newer`. 

## How to push to Github
I keep a copy in a [Github repository](https://github.com/jantsje/website_behavioralethics) 
which is also where this Readme is located. Every time you update the website by pushing to the server, 
you should also push the changes to Git. Try to attach a meaningful message to the changes. I use [Git Bash](https://gitforwindows.org).


You can use `cd` to navigate to the root of the project and `git add .` and `git commit -m "your message here"` and `git push origin master`.

+++
date = '2026-01-22T10:47:26+05:00'
draft = false
title = 'Go static with hugo: Build and Launch Fast'
showToc = true
description = 'Build and launch a blazing-fast static website using Hugo. Learn what Hugo is, why it’s popular, and how to create, customize, and deploy a site to GitHub Pages in minutes.'
+++

![hugo logo](/images/hugologo.png)
# What is hugo?
Hugo is a **static site generator** used to build websites and blogs. **Static** means files are prebuilt. **Static site generator** is a tool, it takes simple Markdown files and turns them into a proper complete site that can be launched.


## Why people like hugo?
- Insanely Fast and secure.
- No database or backend.
- Highly customizable.


## Typical folder structure:
Before proceeding, let's understand the hugo folder structure of your site.
Your site is a folder which have some folders and files that are given below.
```
my-site/
├─ content/
├─ layouts/
├─ static/
├─ themes/
├─ hugo.toml

```

- **Content** ---->
This folder is stuffed with your actual content 
```
content/
├─ posts/
│  └─ first.md
|  └─ second.md
|  └─ third.md
├─ about.md

```
- **themes** ----> A theme is actually a small site inside your hugo site.


- **Static** ---->
Images, fonts and JS are stored in static folder.
Files are copied as it is to final site.

- **Public** ---->
Public is basically your final generated site. This is what you edit.

- **hugo.toml** ---->
It is the main configuration file. It includes the theme name , params , title and baseURL of your site.


---
# Static site generation process:

## Step 1: Installing hugo
- linux
```
sudo snap install hugo
```
> Note : Use snap instead of apt because it will install the latest version of hugo
- Mac OS
```
brew install hugo
```
- Windows 

Select a theme from [Hugo Themes](https://github.com/gohugoio/hugo/releases) and incorporate it:


## Step 2: Creating new hugo site 
1. Run the given command to generate a hugo site and replace site-name with your site name.
```
hugo new site site-name
```

2. Now, remember that from now onward we have perform every step inside our site, so navigate into the site.
```
cd new-site
```
![create new site](/images/hugo-guide1.png)


## Step 3: Theme setup and enabling:
### 1. setting the theme:
1. Initialize git init to track all your changes.
```
git init
```
2. Select your theme from [Hugo's themes](https://themes.gohugo.io/), copy it's https link.
3. Add your theme as a submodule inside your site repo.
```
git submodule add github-url-to-theme themes/theme-name
```

```
git submodule add https://github.com/adityatelange/hugo-PaperMod.git themes/PaperMod
```
![setting the theme](/images/hugo-guide2.png)
4.  Commit these changes with a appropriate commit message.
```
git commit -m "themes: Add PaperMod"
```
### 2. Enabling the theme:
Open your hugo.toml file and enable the theme.

In my situation,
``` 
theme = 'PaperMod'
```


## Step 4: Writing your first blog post
1. You have created your first blog post.
```
hugo new posts/first.md
```
2. Stuff this post with your content by simply opening the first.md file with text editor or any other.

3. Save the content.
![first post](/images/hugo-guide3.png)


## Step 5: Preview the site locally:
Now, launch the site locally.

```
hugo server --noHTTPCache
```
Open the local link that is named as **http://localhost:1313/**.


---

# Deployment to Github:
So, till now your site is locally available. We need to deploy it 
to github to make it globally available.


## Step 1: Create a new repository
1. Navigate to Github.
2. Create a new repository.
3. Give it a name you want for your site in the given manner.

```
username.github.io
```





## Step 2: Push your site to github
After the customization and commits, push your local site to Github repository
1. Open your remote repository.
2. Copy it's https link.
3. The below given command connects your local Git repository to a remote repository on GitHub.
4. Paste your repository https link as given below.


```
git remote add origin https://github.com/<your-username>/<your-username>.github.io
```
For instance,

```
git remote add origin https://github.com/realahnet/realahnet.github.io
```
5. Push the changes to your Github repository.

```
git push -u origin master
```






## Step 3: Setup Github Pages
1. Open your repository and navigate to the settings tab.
2. Proceed to the pages tab
3. Locate the "Build and deployment" section.
4. Here, change the source to " Github Actions".



![setup Github repo](/images/hugo-guide5.png)





## Step 4: Setting the Github workflow
1. Now, switch to the "Actions Tab".
2. Click the option "New workflow".
3. Search for "hugo", configure that file.
![configure](/images/hugo-guide6.png)
4. Update the hugo version to the latest version.
![version update](/images/hugo-guide7.jpeg)
In my case,
```
env:
  HUGO_version : 0.154.5
```
5. Commit the change with an commit message.
6. Afterwards, a workflow will start running.
7. The moment this workflow is successfully deployed, your site is launched at 
```
your-username.github.io
```





## Step 5: Update your site's Base URL:
1. Handle your hugo.toml file.
2. Edit your site's Base URL in the same manner as given below.

```
https://yourusername.github.io/
```

```
baseURL = 'https://velanora.github.io'

```
3. lastly, visit your site from github pages.




![update blogs URL](/images/hugo-guide8.png)

---

# Conclusion
Hugo makes it incredibly easy to build and deploy fast, secure, and modern websites with minimal effort. If you value speed, simplicity, and full control over your content, Hugo is an excellent choice.






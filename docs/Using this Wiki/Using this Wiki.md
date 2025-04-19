---
title: How to update this wiki
parent: Using this Wiki
nav_enabled: true 
nav_order: 1
---

# How to update this wiki

Date Updated: April 15, 2025 8:50 PM

The lab wiki is hosted on the lab’s Github page. These steps will take you through how to update docs and the website:

1. Have a Github account
2. Get added to the lab’s github (the lab is an organization with different members)
3. Make sure you have git installed and your git authentication enabled
    
    Not sure? Click here to see a tutorial on getting git credentials
    
    [Github Primer](https://www.notion.so/Github-Primer-d3686c7bfac9415a9318b17f8bd82439?pvs=21)
    
4. In the terminal run
    
    `git clone https://holmeslab.github.io/holmeslab.git`
    
    1. Or, if you already have it cloned, update to the most recent version by going into the folder where you have the repository cloned and running
        
        $`git checkout main`  Make sure you’re on the correct branch
        
        $ `git pull --rebase origin main` This pulls the most updated version of the repo
        
5. Now navigate to the /docs folder
6. Open the doc you want to edit, or make a new markdown doc
    1. You can make a markdown doc by opening any code editor and creating a new text file, and saving it as .md for markdown
7. Write your doc
    1. Markdown files are written with just normal text. 
    2. Any additional formatting (headings, tables, buttons, bullet lists, etc) can be found in the 
    [markdown tutorial page][https://holmeslab.github.io/holmeslab/UsingThisWiki/UsingMarkdown].
8. Figure out what folder/file you want this file to go under
    1. All files/folders are listed in the navigation bar on the left of the website
    2. The name that appears in the navigation bar which you want it to go under will be the name you’ll put in the “parent” field below
9. Add this at the TOP of your markdown file
(This is because the site is a Jekyll site. Read more about page layouts on the [Jekyll Documentation](https://jekyllrb.com/docs/pages/))
```bash
---
title: <any title> 
	#This is the title which will appear on the nav bar
	#This doesn't have to match any content within the file
	#But is the label which is the 'parent' field for any nested pages
nav_order: 1 
	#This is the order they'll appear in the nav bar, lowest=first
nav_enabled: true 
	#default to true
	#if false the page will still be in the nav bar,
	# but the nav bar won't be *visible* on that page
parent: <any title>
	# if this references an existing 'title' field, the doc will be 
	# located as a nested doc under that doc in the nav bar
---
```

1. Save your markdown file into /docs or any relevant subfolder
2. Update the file back into the github repository like this
    
    `git add your_file.md`
    
    `git commit -m “Note about changes, for example: Adding file.md”`
    
    `git push`
    
3. Github pages may take up to 10 minutes to display the changes
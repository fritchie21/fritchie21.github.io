# fritchie21.github.io
Nemophily Natives Plant Nursery in Auburn Alabama [https://nemophilynatives.com](https://nemophilynatives.com)

# Overview of this repository and what produces the website

There are 2 main types of branches in this repository, because this website is built using Jekyll:

  - The first is the one that contains all of the files that **are the website**. This is generally always the `master` branch. 

  - The next types of branches (e.g., `preJekyll-src`) are the raw files for making a website in Jekyll. So these files **will not**, in general, show up as a nice website in a browser unless you somehow interface with Jekyll.

All changes to the content and styling happen within the second type of branch (e.g., `preJekyll-src`). These files then get run through Jekyll on a personal computer, and Jekyll spits out the files for a website into the `_site` folder. The contents of `_site` then get copied into the `master` branch when it is time to update the website.

# Instructions for Updating

### Be sure to make changes to a branch other than `master` (e.g., in `preJekyll-src`).

To preview the site with drafts on a localhost, run `bundle exec jekyll serve --drafts` with the `--drafts` switch.

```
cd ~/<< FIXME: path to git repository >>/fritchie21.github.io
git checkout preJekyll-src
```

Might want to clean out old _site first
```
rm -rf ./_site
```

as well as index.html
```
rm ./index.html
```


`ENV=production` necessary for Google Analytics code if statement

```
JEKYLL_ENV=production bundle exec jekyll build

rsync -azv --delete /<< FIXME: FULL path to git repository >>/fritchie21.github.io/_site/ /<< FIXME: FULL path to git repository >>/jekyllBuiltSiteFiles

git checkout master
rsync -azv /<< FIXME: FULL path to git repository >>/jekyllBuiltSiteFiles/ /<< FIXME: FULL path to git repository >>/fritchie21.github.io/

git add .
git commit -m "site update TODO time if desired"
git push
git checkout preJekyll-src
```



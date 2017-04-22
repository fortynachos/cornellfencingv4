# Cornell Fencing Website v4

This site is dedicated to the Cornell Fencing Alumni Association.

Stylesheets were shamelessly scraped from http://www.styleshout.com/

![go big red](http://i.imgur.com/9HjTMC5.png)

## Get the code
**Note: Because this is a org-level Github Pages repo, we use the `master` for deployment, _not_ development. Development is done on the `dev` branch.**

Before you do anything:

#### Fork!
On this page, click the "fork" button in the upper-right-hand corner of the page.

#### Clone!
```
git clone (url_of_your_forked_repo)
cd cornellfencing.github.io
git remote rename origin my-fork
```

#### Add an upstream remote!
```
git remote add origin https://github.com/cornellfencing/cornellfencing.github.io
```

#### Confirm!
```
git pull origin dev
```
^^ This should return a message saying your changes are up to date.

## Making edits
The page is actually pretty straightforward.

#### Seeing Your Changes
We use Node.js to run a local dev server. [Install Node.js from the official website.](https://nodejs.org/en/) Get version 7.x.

In the directory for this project:

```
# Install the dependencies
npm install

# Launch the server
npm start

# You'll see an output like:

> cornellfencingv4@1.0.0 start /Users/nickheiner/Code/cornellfencingv4
> static -a 0.0.0.0 -H '{"Cache-Control": "no-cache, must-revalidate"}' app

serving "app" at http://0.0.0.0:8080
```  

Go to the URL listed in the output (`http://0.0.0.0:8080` in the example above) to see your page. Hit "refresh" when you make any changes to the files on disk.

#### Making text edits
Most, if not all text changes can be made in the `app/index.html` file.  Nothing complicated here, just find the relevant HTML tags and change away.

#### Styling Changes
Looking to change the CSS?  All CSS overrides beyond the defaults should be made in `app/css/layouts.css`.  The other CSS files shouldn't need to be touched unless you very explicitly know what you're doing.

#### Adding Images
Dump all new image assets in the `app/images` directory and source them in index.html.  For something like adding images to the scrolling hero image, add the image URL in the format in `app/css/layouts.css` (under '0. Alumni Hero Banner Images'), and then add the relevant id to the index.html file.  Search "team-2015" if you're looking for an example in that file.  

#### JS changes
This page uses a lot of out-of-the-box js libraries that I didn't really make any effort to change.  Nearly of the javascript-based behavior of the page is powered by [Foundation Zurb](https://foundation.zurb.com), and secondarily supported by jquery.  If you're looking to change the JS on your own, no groundwork has really been laid out for you, so please follow general best practices and try not to make a mess.

## Commit / Push
First check your commits with diff and status
```
git diff
git status
```
^^ Diff will return all of the individual lines you have changed. Status should return the files you have modified, added or deleted. If you added or deleted a file in the directory make sure to use git add <file> or git rm <file> so git will add or delete them properly. Once that is done you can commit and push. If you do not want to commit all the changes you made list them by name with git commit -m instead of git commit -am.

```
git pull origin dev
git commit -am "Your commit message"
git push my-fork dev
```

Once you've done that, click "New pull request" on the github.com website for your fork to make a pull request to the cornellfencing/cornellfencing.github.io repo for review.

## Deploying
First, ensure that the git remote `origin` refers to the cornellfencing/cornellfencing.github.io repo:

```
$ git remote -v | grep origin
origin	git@github.com:cornellfencing/cornellfencing.github.io.git (fetch)
origin	git@github.com:cornellfencing/cornellfencing.github.io.git (push)
```

If that didn't look right, use:

```
$ git remote set-url origin git@github.com:cornellfencing/cornellfencing.github.io.git
```

After that's done, you're ready to deploy:

```
npm run deploy
```

This will push the contents of the `app` directory to Github pages. It will take a few minutes for the updated site to be live. GH Pages caches, so you may need to clear your browser cache before you see the updates.

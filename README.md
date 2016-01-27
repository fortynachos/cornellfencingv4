Cornell Fencing Website v4
=========================

This site is the fourth reincarnation of the cornell fencing website, this time dedicated to the Cornell Fencing Alumni Association.

Stylesheets were shamelessly scraped from http://www.styleshout.com/

![Cornell Fencing](https://camperregsecure.com/cornellcampslogin/css/cornell-logo.png "Cornell Fencing")

## Get the code
Before you do anything:

#### Fork!
On this page, click the "fork" button in the upper-right-hand corner of the page.

#### Clone!
```
git clone (url_of_your_forked_repo)
```

#### Add an upstream remote!
```
git remote add upstream https://github.com/fortynachos/cornellfencingv4
```

#### Confirm!
```
git pull upstream master
```
^^ This should return a message saying your changes are up to date.

## Making edits
The page is actually pretty straightforward.  

#### Making text edits
Most, if not all text changes can be made in the ```app/index.html``` file.  Nothing complicated here, just find the relevant HTML tags and change away.

#### Styling Changes
Looking to change the CSS?  All CSS overrides beyond the defaults should be made in ```app/css/layouts.css```.  The other CSS files shouldn't need to be touched unless you very explicitly know what you're doing.

#### Adding Images
Dump all new image assets in the ```app/images``` directory and source them in index.html.  For something like adding images to the scrolling hero image, add the image URL in the format in ```app/css/layouts.css``` (under '0. Alumni Hero Banner Images'), and then add the relevant id to the index.html file.  Search "team-2015" if you're looking for an example in that file.  

#### JS changes
This page uses a lot of out-of-the-box js libraries that I didn't really make any effort to change.  Nearly of the javascript-based behavior of the page is powered by [Foundation Zurb](https://foundation.zurb.com), and secondarily supported by jquery.  If you're looking to change the JS on your own, no groundwork has really been laid out for you, so please follow general best practices and try not to make a mess.

## Commit / Push
```
git pull upstream master
git commit -m "Your commit message"
git push origin your_branch
```

Once you've done that, make a pull request to the fortynachos/cornellfencingv4 repo for review.

## Deploying
We use a delightful webhosting interface called cPanel, hosted by Lunarpages.  You have two options for deployment:

#### The cPanel UI
You can access cPanel by going to https://OBI.lunarbreeze.com:2083/ and entering in our credentials.  Since this is the internet, I won't post said credentials here.  Contact Mike Fotinatos if you need them.  

This method is good for uploading entire directories.  Just zip up your app directory:

For mac/unix people:
```
tar -zcvf app.tar.gz app
```

Then go ahead and log into cPanel.  Once you've logged in, go to the "File Manager" and choose the web root option. Then go to the cornellfencingassociation directory, upload your zipped file, right click it, and click extract.  You may want to rename the existing app directory to something else unless you're sure that the version you're uploading is stable.

Rename the extracted folder to ```app```, **and then copy the .htaccess file from the /public_html/cornellfencingassociation directory into your new app folder**.  If you don't do this, your page will get a 500, and everything will be sad.

Once you do this, you're done!

#### The FTP

For those of you who want to point edit a few files and hate clunky UIs:
```
ftp corne49@cornellfencing.com
(Enter the credentials Mike gave you)
cd public_html/cornellfencingassociation
```

And you're in!  Go ahead and start uploading your files.  You're dealing with a standard unix ftp, if you're curious about which commands would work.

Ruby on Rails with Sublime Text 3
===============

Getting Started
--------

Sublime doesn't work as well as Rubymine right out of the box, but with some  configurations this will become a whole different story. 

### Install ST3
While we have the license for Sublime Text 2, I recommend using Sublime Text 3. It supports **jump to definition** which was a missing feature in ST2 and has kept some of us from switching away from Rubymine. It also has a bunch of performance enhancements. [Download Sublime Text 3](http://www.sublimetext.com/3)

### Use **subl** in command line. 
`subl <filename>` opens a specified file and `subl .` opens the current directory in ST3. This will also come in handy when setting up a default editor in other systems, for example, when specifying the editor for the `edit` command for **Pry**. 

* Maverick: 
     sudo ln -s /Applications/Sublime\ Text.app/Contents/SharedSupport/bin/subl /usr/bin/subl
* Earlier version of OSX:
    sudo ln -s "/Applications/Sublime Text .app/Contents/SharedSupport/bin/subl" ~/bin/subl


### Install [Package Control](https://sublime.wbond.net/installation) 
The very next thing that should be installed after ST3 itself.  Once installed, `press ⌘⇧P, type 'inst', hit 'enter'` to browse the list of available packages; similarly, `press ⌘⇧P, type 'remo', hit 'enter'` to remove an installed package. 

You can also find all [the compatible packages](https://sublime.wbond.net/browse) in the package control website.  


### Use a theme
A `Theme` is different from a `Colour Scheme`. A good theme can dramatically improve the look and feel of the editor. Besides the infamous [Soda theme](https://sublime.wbond.net/packages/Theme%20-%20Soda),  it's also worth to look at [Phoenix](https://sublime.wbond.net/packages/Theme%20-%20Phoenix) and [Spacegray](https://sublime.wbond.net/packages/Theme%20-%20Spacegray). I use [Flatland](https://sublime.wbond.net/packages/Theme%20-%20Flatland) myself. 

After installing, you need to specify a theme to use under `Settings - User`:
```json
"theme": "Flatland Dark.sublime-theme"
```

If you want to further enhance the look and feel of your ST3, [this](http://webdesign.tutsplus.com/articles/simple-visual-enhancements-for-better-coding-in-sublime-text--webdesign-18052) is an excellent blog post for the very purpose. 

----------


Backup ST3 with Google Drive
--------

ST3 is a configuration heavy editor, and thus it's important to backup your settings. With some initial setup, Google Drive or Dropbox can backup your ST3 settings automatically to the cloud, allowing you share the same set of settings across different computers.

### `Settings - Default` VS. `Settings - User`
Everytime ST3 updates, `Settings - Default` will be **reset**, meaning that every change made in it prior to the update will be removed, hence it's important to put all settings in `Settings - User`, and only use `Settings - Default` as a reference. 

### Set up the backup
The steps below should to be done on the computer that has your most up-to-date ST3 settings (the ones you want to propagate to other computers).

Before doing anything, close ST3, just to be clean.

```
# Create the sync directory in Google Drive
$ mkdir ~/Google\ Drive/sublime-text-3/

# Move your ST3 "Packages" and "Installed Packages" to Google Drive
$ cd ~/Library/Application\ Support/Sublime\ Text\ 3
$ mv Packages/ ~/Google\ Drive/sublime-text-3/
$ mv Installed\ Packages/ ~/Google\ Drive/sublime-text-3/

# Then symlink your Google Drive directories back locally
$ ln -s ~/Google\ Drive/sublime-text-3/Packages/
$ ln -s ~/Google\ Drive/sublime-text-3/Installed\ Packages/
```

Note that ST3 has three other directories under `~/Library/Application Support/Sublime Text 3/`: Cache, Index and Local. **Do not** sync these, each computer should manage their own local copies.

### Syncing other computers
All other computers will now have ~/Google Drive/sublime-text-3/. Follow these steps on each of the computers you have ST3 installed to sync them:

```
# Remove the "outdated" directories
$ cd ~/Library/Application\ Support/Sublime\ Text\ 3
$ rm -rf Packages/
$ rm -rf Installed\ Packages/

# Then symlink your Google Drive directories back locally
$ ln -s ~/Google\ Drive/sublime-text-3/Packages/
$ ln -s ~/Google\ Drive/sublime-text-3/Installed\ Packages/
```

Now when you tweak to your Sublime Text 3 settings, they will propagate automatically. Even new packages get installed everywhere!


----------


Import projects into ST3
-------

How many projects do we work with actively? How many projects do we work with simultaneously? Switching between projects was a pain for me, but after importing them into ST3 the task became a lot easier. 

### Importing the projects:

#### Open a project in ST3
You can do so by navigating to `File -> Open` or by using the `subl` command we set up earlier. 
```
$ cd ~/<your project root>/mysageone_na
$ subl .
```
#### Save the project as a ST3 project.
This can be done under `Project -> Save Project As...`; or you can press `⌘⇧P`, type in `psa` and hit `enter`. 

> **Note:** An ST3 project can be named to anything you want, but it's easiest to simply *keep it the same* as the `project directory name`, which in our case is also the `git repository name`. 

After converting one project, you can go ahead and do the same to all our other projects. It's a tedious process but consider it as an one time effort, and it does not even compare to the time it will save in the long run. 

### Switching between projects
Once all the project are set up, you can use the `Quick Switch Project` feature in ST3 to switch between them. You can find it under the `Project menu`, but it's not quick enough until bound to a shortcut:
```
{ "keys": ["f2"], "command": "prompt_select_workspace" }
```
Put the this line in `Key Bindings - Users`.  `f2` can be changed to any key combination you prefer. 

Now if you want to switch between projects, you just need to hit `f2` then type a couple letters from the name of the project you want to switch to:

```sequence
na_sage_one->sageone_us: f2 + 'sus'
sageone_us->mysageone_na: f2 + 'mna'
mysageone_na->mysageone_ca: f2 + 'mca'
mysageone_ca->na_sage_one: f2 + 'nsa'
```
Now it's really up to you to decide how to use this. 








> Written with [StackEdit](https://stackedit.io/).
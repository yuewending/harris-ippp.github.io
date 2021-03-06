# Windows Install Instructions

Please complete the cygwin installation before the first class!

### Cygwin (Terminal)

* Go to https://cygwin.com/install.html
* Download the 64-bit version ([setup-x86_64.exe](https://cygwin.com/setup-x86_64.exe)) and open it.
* Click through the first setup window (Cygwin Setup).
* "Choose Installation Type" → "Install from Internet."
* "Choose Installation Directory" → whatever you'd like, but the default (C:\cygwin64) is good.  If you're updating an existing installation, be careful to ensure that it is the same location as your current copy!
* "Select Local Package Directory" → again, whatever you'd like, but the Downloads default  is good.
* "Select Connection Type" → "Direct Connection"
* "Choose Download Sites" → any are fine.
* "Select packages."  Switch "View" to "Not Installed."  Pay attention here: what you're doing is selecting the "additional prorams that you'll want!  
   * search "sqlite3".  For "sqlite3: Client program for accessing SQLite3 databases", click on "Skip" that it says 3.20.1-1 (or so), instead of "Skip".
   * search "git".  For "git: Distributed version control system", click on "Skip" that it says 2.14.0-1 (or so), instead of "Skip".
   * search "python3".  Click on "python3: Py3K language interpreter" to replace "Skip" with (~3.6.1-1).
   * search "curl".  Click on "curl: Multi-protocol file transfer tool" to replace "Skip" with (~7.55.1-1).
   * search "unzip".  Click on "unzip: Info-Zip decompression utility" to replace "Skip" with (~6.0-17).
   * Next.
* If it comes up: "Resolving Dependencies" → Next.  (i.e., leave "Select required packages (RECOMMENDED)" checked.)
* The setup will now start "spinning."  Give it some time.
* "Installation Status and Create Icons" → Up to you ("Finish").  I do have the icons.

Bonus: if you need to install additional packages, you can just run the exact same cygwin installer, over and over again, adding the extra packages you want (e.g., curl).

### Anaconda
* Go to https://www.continuum.io/downloads.  Download and open the 64-bit installer.  (Don't give them your email!)
* Setup: Next.
* "License Agreement" → Agree to the terms and conditions.
* "Select Installation Type" → Just Me (recommended).
* "Choose Install Location" → Default is probably fine.  *Make a note of where it goes.*  In my case:
   * `C:\cygwin64\home\<YOUR_USER_ID>\Continuum\Anaconda3`  (`<YOUR_USER_ID>` is actually your user id, not that string.)
* "Advanced Installation Options" → just accept. "Install."  (Let it go.)
* Learn about Anaconda cloud only if you feel like it (no).
* Now, open up cygwin.  You will be at /home/\<YOUR_USER_ID\>/.  Type `which python`.  It will probably _not_ be the one you just installed.
   * Using Atom, open up the file `.bashrc`, which should be in `/home/UserName/` in your cygwin directory: in my case, `C:\cygwin\home\jsaxon\.bashrc`.
   * At the end of this fille, add and save (with an appropriate substitution for the path)
      ```
      export PATH=/cygdrive/c/the/path/to/your/Continuum/Anaconda4:/cygdrive/c/the/path/to/your/Continuum/Anaconda4/Scripts:$PATH
      ```
   * What is this doing?  The `.bashrc` file runs every time you open up a terminal, to initialize your environment.  We want to modify that initialization.  The `PATH` is the list of places, separated by colons, where the computer looks for programs.  Your computer may have found `python` before, if there was some copy of `python` on your machine.  But you want it to first find (and therefore _use_) this new copy from Anaconda, which has these nifty doodads that we'll use later in the course.  By running `export PATH=...`, you are updating your `PATH` accordingly.  
* Now, when you open cygwin, you should be able to get a python prompt via `python -i` (return) (it should say "Python 3.6.2 |Anaconda 4...").
* Finally, let's make sure that Jupyter can be started easily.
  * Search for it in the start menu, then right-click, and select "Properties."  (See pictures, below.)
    * If you're on Windows 10, I think you will need to first click on "Show in Folder," and then again right click to see "Properties."
  * Change the target field to the following, _with appropriate substitutions_!  By "appropriate substitutions," I mean that you will replace the final path in this string to where you want juptyer notebooks to launch.
    The earlier parts will be different from mine -- they are on your computer.
    The last bit -- the final path -- is where you want to the notebook to launch, and it is the only part you will change.
    You _will not_ change the earlier paths.
    ```
    C:\cygwin64\home\jsaxon\Conda\python.exe "C:/cygwin64/home/jsaxon/Conda/Scripts/jupyter-notebook-script.py" --NotebookApp.iopub_data_rate_limit=100000000 C:\WHERE\YOU\WANT\TO\LAUNCH
    ```
    Note that your classmates with Macs will simply launch `jupyter notebook`.  You should not do this, as it will launch multiple servers that are a pain to kill, and a potential security hole.
    
#### Geographic Libraries
We'll want a few more libraries for week 10, that depend on some geographic libraries.  These have to be installed in their own environment.  We'll do this through the Anaconda Navigator program.

* Open Anaconda Navigator
* Go to "Environments" on the left hand side.

![](img/w_geo_a.png?raw=true)

* At the bottom, click "Create"

![](img/w_geo_b.png?raw=true)

* Name it py35 (or anything).  Select python version 3.5. Click create.

![](img/w_geo_c.png?raw=true)

* Click on "Channels" on the right hand side, then "Add."  Type "conda-forge" and "Update channels."

![](img/w_geo_d.png?raw=true)

*  Switch the packages to "Not installed."  Then search for and check: geopandas, geopy, requests, and folium.  Requests may already be installed.

![](img/w_geo_e.png?raw=true)

*  After doing this, you should be able to switch to "Selected," and see all four packages.  (Except of course, requests, if it was already installed.)

![](img/w_geo_f.png?raw=true)

*  Click "Apply" in the bottom left hand side, and then confirm in the dialog.

![](img/w_geo_g.png?raw=true)

* In the future, you will launch jupyter notebooks for geographic work (only) by first clicking on the in _this environment_ (py35), and then clicking on the "Play" icon to "Open with Jupyter Notebook."  The notebook that then opens should be able to run you test-suite.ipynb.

![](img/w_geo_h.png?raw=true)

    
**You're done the python part!  Go back to the [main instructions](README.md) to check that the install worked out!!**

### Atom Install
* Go to atom.io and download the Windows installer.  Launch it.  It is that easy!
* Installing a "de-linter" to find bugs in your code will help a lot.  Go to settings (Ctrl+Comma) and click on "Install."  Then search for "linter-pylint" and install it with all of the dependencies that come up.  Now whenever you save a python file, it will (partially!!) check your work!

### GitHub Account
* Create a [student GitHub account](https://education.github.com/pack), or just a standard GitHub account.  You will use this account to push (submit) all of your work.
  You have already installed the command line git, through cygwin.
* Finally, to make submission easier, you should "create an ssh key" key for your GitHub account.
  This is just the way that the git encrypts communication (lets you download files);
    `ssh` (secure shell) is the standard way that we make secure connections from the command line.
  Follow GithHub's instructions to 
   1. [generate a new ssh key](https://help.github.com/articles/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent/#platform-windows)
      * If you have trouble creating the passphrase when the time comes ... don't (just leave it blank/hit return).  By providing the `id_rsa.pub` to GitHub, you're permanently telling it the call and response (Marco/Polo) so that it knows your computer is _you_.  This last piece is not a prerequisite for starting on Monday, but _will_ be necessary, for downloading and starting your homework.
   2. [add it to your GitHub account](https://help.github.com/articles/adding-a-new-ssh-key-to-your-github-account/#platform-windows).
      * If `clip` doesn't work, the piece that you'll paste into the GitHub site, is the output of `cat ~/.ssh/id_rsa.pub`.
  
  In these instructions, you'll see a few lines that bein with a $ or #. Typically in coding instructions, $is understood to be your prompt, and anything following a # is a comment. This means that you don't copy the $-sign itself, and you completely skip the lines beginning with a # -- though they will actually do nothing if run.
* Tell GitHub who you are, by executing from the command line (Terminal):
  ```
  git config --global user.email "you@example.com"
  git config --global user.name "Your Name"
  ```

![Start](img/jupyter_start.png?raw=true "Start")
![Properties](img/jupyter_properties.png?raw=true "Properties")


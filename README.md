#Paul's Vim & PHP Stuff#

This project contains an updated version of the php.vim syntax file distributed with VIM. The list of PHP keywords, constants, functions, and classes are updated to be current with current stable version of PHP (5.5 as of last commit).
I started maintaining this after PHP 5.3 came out and the stock VIM syntax file was not updated. The distributed version only covers up to PHP 5.1.4 and since then **many** new features and classes have been added.
In addition I simplified the file, removing several sections that are not often used (at least by me) such as automatic folding of all control structures and ASP tags support. I also removed several switches designed for backwards compatibility  with VIM 5.X and 6.X. Lastly I generated the list of constants, functions, and classes by reflecting PHP itself. See the `php_vimgen.php` section below for more explanation.

Vim will use this `php.vim` when you open up a PHP file instead of the distributed one. And since it is in your home directory it won't get wiped out when up update vim. Lastly you can always revert to the distributed version by deleting or renaming the file.

##Installation:##
Use Pathogen.vim or
Create the following directory if it does not already exist and place `syntax\php.vim` inside of it.

* Unix: `/home/<username>/.vim/syntax/`  
* Windows up to & incl XP: `C:\Documents and Settings\<username>\_vim\syntax\`  
* Windows Vista & 7: `C:\Users\<username\_vim\syntax\`

##php_vimgen.php##
In order to generate the list of functions, classes, and constants I created a script that uses reflection to get these items. That script is included in the project as well. It will generate a file with the format and keywords for the Vim syntax highlighting. All you have to do after running it is copy and paste the contents of the generated file into `php.vim`.
Before running `php_vimgen.php` open it up and adjust the output file location and name in the `$out_file` variable at the top of the file. You will also want to adjust the list of extensions to generate syntax for. Just uncomment ones you want and comment out ones you don't. Or you can pass command line arguments to the script (contributed by https://github.com/FilipeD). Note that if the extension is a dynamically loaded one and php can't load it the script will error out with out completing.
Run `php php_vimgen.php` from your shell to make the file or see below.

###Usage:###
The output file and selected extensions can be defined in two ways - by editing variables inside of `php_vimgen.php` or by passing command-line arguments to the script. CLI options override the variables inside the script.

* `--out` sets the output file, overrides `$out_file`, can be relative or absolute path:
```php php_vimgen.php --out /path/to/foo.bar```

* `--ext` overrides `$extensions`, separate extension names with a comma or space character:
```php php_vimgen.php --ext 'mysql,bz2,core'```

* `--merge` paired with `--ext` merges to, instead of overriding, the default `$extensions` list:
```php php_vimgen.php --ext 'interbase,posix,readline' --merge```

* `--not` excludes extensions (set in the file or through command-line argument):
```php php_vimgen.php --ext 'readline,wddx' --not 'intl,tidy,xml'```

##.vimrc File##
As an additional detail I have placed my `.vimrc` file in this project (now inside the `extras` directory for Pathogen people). It is not too special
but setup to serve my needs nicely. CAUTION: I have Ctrl-X, Ctrl-C, Ctrl-V, and Crtl-Z remapped to Cut, Copy, Paste, and Undo like on Windows, because that is what I am used to. I used GVIM on Windows a lot before switching to Linux at home and still use it at work. The only other possibly novel thing is that I have `make` setup to do a `php -l` lint check on the current file if it is a php file. I got that from someone else in the PHP community. And I set <tab> to 2 spaces in Javascript and HTML files.
Note that until Fall of 2013 I was using different `.gvimrc` and `.vimrc` files. That caused problems when I started using Pathogen and some other plugins so I just have some `if has("gui_running")` switches in there. During this time I also started using Pathogen, VIM Airline, and NERDtree.

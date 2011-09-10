#php-vimgen#

Thi project contains an updated version of the php.vim syntax file distributed with VIM.
The list of PHP constants, functions, and classes was updated to be current with PHP 5.3.
Many new classes were added in the 5.2 branch and the distributed version only covers up
to 5.1.4. In addition I simplified the file, removing several sections that are not often
used (at least by me) such as automatic folding of all control structures and ASP tags
support. I also removed several switches designed for b/c with VIM 5.X and 6.X.

##installation:##
Create the following directories if they does not already exist and place php.vim inside of it.
Unix: `/home/<username>/.vim/syntax/`  
Windows up to & incl XP: `C:\Documents and Settings\<username>\_vim\syntax\`  
Windows Vista & 7: `C:\Users\<username\_vim\syntax\`

##usage:##
The output file and selected extensions can be defined in two ways - by editing php_vimgen.php,
or by passing command-line arguments to the script:

* `--out` sets an output file:
```php php_vimgen.php --out foo.bar```

* `--ext` overrides `$extensions`, separate extension names with a comma or space character:
```php php_vimgen.php --ext 'mysql,bz2,core'```

* `-m` paired with `--ext` merges to, instead of overriding, the default `$extensions` list:
```php php_vimgen.php --ext 'interbase,posix,readline' -m```


* --not excludes extensions (set on the file or through a command-line argument):
```php php_vimgen.php --ext 'readline,wddx' --not 'intl,tidy,xml'```


Vim will use this `php.vim` when you open up a PHP file instead of the distributed one. And
since it is in your home directory it won't get wiped out when up update vim. Lastly you
can always revert to the distributed version by deleting or renaming the file.

In order to generate the list of functions, classes, and constants in PHP 5.3 I created a
script that uses reflection to get these items. That script is included in the project as
well. It will generate a file with the format and keywords for the Vim syntax highlighting
included. All you have to do is copy and paste the contents of the generated file into
php.vim. Before running open up the file and adjust the output file location and name.
It is saved in a variable at the top of the file. You will also want to adjust the list
of extensions to generate syntax for. Just uncomment ones you want and comment out ones
you don't. Note that if the extension is dynamically loaded and php can't load it the
script will error out. Run `php php_vimgen.php` from your shell to make the file.
 
As an additional detail I have placed my `.gvimrc` and `.vimrc` files in this project. They
are not too special but setup to serve my needs nicely. CAUTION: I have Ctrl-X, Ctrl-C,
Ctrl-V, and Crtl-Z remapped to Cut, Copy, Paste, and Undo like on Windows, because that
is what I am used to. The only other possibly novel thing is that I have `make` setup
to do a `php -l` lint check on the current file if it is a php file. I got that from
someone else in the PHP community. I never could get the `omnifunc` function signature
stuff working right.

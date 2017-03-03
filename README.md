# Roll Your Very Own Gopherspace!

## What is This? 
This is a technical primer that gives you a crash course on how to setup and create a simple gopherspace. It is by no means an in-depth article.

## Who is This For? 
* Anyone with a basic knowlege of Linux wanting to try thier hand at building their very own gopherspace.
* Geeks that are frustrated by the lack of documentation on Gopherspaces and spent the last 2 hours Googling for solutions to no avail

##  What is Gopher? 
Check out this [article](https://github.com/sgolovine/roll-your-gopher/blob/master/AboutGopher.txt) from Floodgap (Dec. 2000) 

------------------

###  Prerequisites:

1. Ubuntu or another Linux distribution
2. Python 2.2+ (most distros come with Python preinstalled)

It should also be noted, if you use a programming text editor that remaps TAB to a number of spaces, you want to make sure that feature is disabled.

Although not required, I also highly recommend Firefox + OverbiteFF, it's a simple extension that lets you browse gopher:// sites using Firefox. 

[Get OverbiteFF](http://gopher.floodgap.com/overbite/) 

### Installing Gopher

There are many packages for Gopher these days. For the sake of this document we will be using  [PyGopherd](https://github.com/jgoerzen/pygopherd). If you are using Ubuntu or a Debian derivative distro you can install the `pygophered` package via:
	
	sudo apt-get install pygopherd
	
Alternatively, you can install it from the Github Repository. I wont be getting into that in this article but the [PyGopherd](https://github.com/jgoerzen/pygopherd) PyGopherd repo gives pretty good instructions on how to do so. 

Once installed, navigate to `localhost:70` (or the ip address of the server you installed it on) to confirm that it's working.


### Gopher Daemon and Configuraton Information

Here are some useful commands and location relating to the gopher installation.

*NOTE: These locations/commands are related to the pygopherd package, this might differ if you are using another package for gopher*

Gopher Conf: `/etc/pygopherd/pygopherd.config`

Gopher Folder: `/var/gopher`

Gopher Service: `/etc/init.d/pygopherd`

You can start/stop/restart the service using:

	sudo /etc/init.d/pygopherd start
	sudo /etc/init.d/pygopherd stop
	sudo /etc/init.d/pygopherd restart
	
#### Changing Default Gopher Directory

By default, the directory where your gopher-related files are stored is in `/var/gopher`. To change this directory open up `pygopherd.config` and change the line `root=/var/gopher` to your desired directory (located around line 120 in the conf).

### Adding Content

Now that you have gopher up and running, you might be wondering how to add content to it.

Gopher is remarkably simple to write content for in that unlike traditional sites, you don't actually have to write any code per-say. In your default directory, if you remove the `gophermap` file and just start adding content like Text Documents, folder and pictures, Gopher will automatically pick those up and display them. 

However the `gophermap` file can be quite useful. It acts as an `index.html` but for Gopher sites, giving you more control over structure and letting you add text to your pages.


#### Gophermap file syntax

This is my gophersite file:

```plaintext

Welcome to my Gopherspace! 

My name is Sunny Golovine and I am a Computer Science Senior 
at Georgia Southern University currently looking for my next great opportunity after I graduate this May.



Learn more about me:

0About Me	about.txt
1Projects	/projects
0Contact Me	contact.txt


1Programmer Humor	/prghumor



Some external links:

hMy Github	github.html
hMain Site	mainsite.html


Want to view this website using the gopher:// protocol rather than through a web interface?
Check out OverbiteFF, a Firefox extension for viewing gopher:// sites

hOverbiteFF	overbite.html

If you're interested in making your own gopher server read my quick guide on setting it up (Updated March 2017)

0Rolling Your Own Gopherspace	gopherspace.txt

```


#### Adding Links
As you can see nothing too complicated. The only special syntax is for adding links. Here's the basic template

	<filetype>Link Name<TAB>location
	
So if I wanted to add a link to a text file called `foo.txt` id use this:

	0Foo<tab>foo.txt 

To link to another directory:

	1NewDirectory<tab>/newdir
	
Below is a table with all the supported gopher filetypes

|Itemtype |Description      |
|---------|-----------------------|
|0        |text             |
|1        |gopher menu      |       
|5        |zip file         |          
|7        |search server    |                             
|9        |generic binary   |                                  
|I        |generic image    |                             
|g        |gif image        |                           
|s        |sound/audio file |                               
|h        |html             |  

Adding any filetype follows the basic syntax above. 

#### Using Additional Gophermaps

You can use additional gophermaps in subdirectories just like you did in your root. So if I created a directory called `foo`. I can set the directory structure inside of it using another gophermap. Just like I did for my root directory. 





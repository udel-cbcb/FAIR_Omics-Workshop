# FAIR_Omics-Workshop
Welcome to the FAIR Data Practices for Omics Analysis workshop. 

Technological advances in instrumentation for generating genomics, proteomics, and related data have made these high-throughput, data intensive technologies an indispensable part of biological research.  Concurrent advances in computational infrastructure and data science methodologies have not only allowed analysis of these data for their original purpose, but have enabled subsequent reanalysis of such data by other investigators to meet other scientific objectives.  This emerging paradigm has underscored the need for practices that make such data Findable, Accessible, Interoperable, and Reusable (FAIR).  This workshop will provide primarily laboratory based scientists with the knowledge and tools they need to apply FAIR practices in their own research.

## Setup

### Slack

The [Slack platform](https://slack.com) is the preferred method for communicating during the workshop.  You can use Slack in a web browser or [download](https://slack.com/downloads/) the desktop app.  If you haven't used Slack before, check out [this guide](https://slack.com/help/articles/218080037-Getting-started-for-new-Slack-users) for getting started.

### Obsidian

We will be using [Obsidian](https://obsidian.md) for documentation purposes in this workshop.  Obsidian is available for Windows, Linux, and MacOS.  Downloads can be found [here](https://obsidian.md/download).

### Git

To clone this repository, you will need to install git on your computer.

### Biomix

To connect to Biomix, you will need an ssh client.  Additional Biomix documentation can be found [here](https://bioit.dbi.udel.edu/BIOMIX/BIOMIX-cluster.html).

**MacOS and Linux users**

MacOS and most Linux distributions come with ssh clients already installed.  To connect to Biomix on these systems, open your terminal and use the `ssh` command with your username and the name of the server:

```bash
ssh [username]@biomix.dbi.udel.edu
```

Hit enter and type your password when prompted.  For security reasons, your password *will not appear as you type*.  But, your password is being entered and the backspace key will work if you make any errors.  Hit enter.

You should now be on Biomix!  A successful login will result in a few messages,
including “Welcome to BIOMIX.”  Type `logout` and hit `enter` to logout of
Biomix.

**Windows users**

Windows machines often require installation or activation of an ssh client.  

If using Windows Terminal, [follow these steps](https://docs.microsoft.com/en-us/windows/terminal/tutorials/ssh) to activate and configure the ssh client.  If using Windows PowerShell, [follow these instructions](https://docs.microsoft.com/en-us/windows-server/administration/openssh/openssh_install_firstuse) instead.  Once you have activated the ssh client, follow the instructions in the "MacOS and Linux users" section to connect to Biomix.

Alternatively, you can use PuTTY, which is a free ssh client for Windows. It's old-school, but easy to install and use.  

* To use PuTTY, first [download](https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html) the 64-bit version.  
* Open the installer file and follow the instructions. It is convenient to create a
shortcut on your desktop during installation.  
* Start PuTTY by double-clicking on the icon for the desktop shortcut. In the “Host Name” box, enter biomix.dbi.udel.edu. Make sure the port box contains the number 22.  
*  Hit “open.”  A new window should appear.  Enter your Biomix username.  Hit enter.
*  Enter your password when prompted.  Your username will appear as you type it but you will not be able to see your password as you type.  This is normal and you should enter your password as if you could see it.  The backspace key works as well, in case you make a mistake.  Hit enter.
*  You should now be on Biomix!  A successful login will result in a few messages,
including “Welcome to BIOMIX.”  Type `logout` and hit `enter` to logout of
Biomix.

### FileZilla

FileZilla is a Graphical User Interface (GUI) that allows you to transfer files from your local computer to a remote server, and vice versa.  Visit [this link](https://filezilla-project.org) to download FileZilla.

### R and RStudio

If you already have R installed, make sure you have at least version 3.5.3 or above. To download R, go to [this page](https://cran.r-project.org/mirrors.html) and click on the link of the institution closest to you geographically (should be [Carnegie Mellon's](http://lib.stat.cmu.edu/R/CRAN/)).  Then, download R by clicking the link for your operating system.  Finally, open the downloaded installer and follow the onscreen instructions. 

To download RStudio, visit [this link](https://www.rstudio.com/products/rstudio/download/) and download RStudio Desktop (free).  If you are using Windows 8 or earlier, visit [this link](https://www.rstudio.com/products/rstudio/older-versions/) instead and download the installer for version 1.2.5042.  Open the installer and follow the onscreen instructions.  RStudio will automatically recognize the version of R you installed on start up.

## What to do if you have a question

### During in-person sessions

### Not during in-person sessions

Before reaching out on Slack, please try to troubleshoot any errors yourself!

* Google your error.  Working through errors is a valuable skill and you’re more likely to remember the solution this way.  There are lots of resources online including StackExchange, BioStars, software manuals, and Github issues.
* Look out for typos.  Check that your script or command matches those provided.
* Check log files.  Some programs print errors to log files rather than the screen.  If you produced a log file in a script and didn’t get the desired outcome, check the log files.

## Sponsors

Hosted by the UD Chemistry-Biology Interface Program and Center for Bioinformatics and Computational Biology.  This workshop is offered free of charge with support from the NIH National Institute for General Medical Sciences (T32GM133395-03S1).
# Academic dropbox

## The problem

The majority of research users store the majority of their live data on local disks, with little or no redundancy, leaving them open to data loss through accident or theft. To solve this problem, we provide research users with high resilience, high performance, high capacity network storage, but in spite of these advantages, they often don't use it as well as they might.

Another requirement is for easy sharing of files. Most data sharing still takes place via email.

The main reason for this is that many researchers do a lot of work on their laptops, in locations where their network connection may be intermittent, slow or completely sent. On the train, on a plane, in a cafe, they need access to some or all of their data wherever they are.

When faced with this problem, many researchers turn to Dropbox because it is easy to use and requires no user interaction beyond the initial setup. However, there are serious issues with using Dropbox to store research data, primarily the fact that confidential data is being stored on servers outside the institution's control.

What is needed is a tool to transparently synchronise local and network storage, effectively providing an offline cache which provides the convenience and speed of local disk access combined with the resilience of network attached storage.

## Desired features

### Control over storage locations

For confidential research data, it is highly desirable for all copies to remain under the control of the institution(s) who are responsible for looking after it. Any solution should at least have the option of storing data on a university-run storage service.

### Encrypted network transfer

Control of the storage locations on their own is not sufficient. If data is sent over the internet with weak (or worse non-existent) encryption, it can easily be intercepted by an attacker. Strong encryption should be used to protect all data.

### Large file support

Many of the files which researchers routinely work with may be tens or hundreds of megabytes, or in some cases gigabytes or terabytes. Clearly, there's a limit to this - it's reasonable to expect that researchers will have to manage files of a gigabyte or more differently. But a suitable solution should at least work well for files of tens or hundreds of megabytes.

Two things may be important here. First, the user needs feedback about the progress of a sync so that they aren't surprised when changes they were expecting haven't propagated yet. Second, the tool needs to gracefully handle a user cancellation or a dropped connection without losing or corrupting data. Ideally, if this happens it should be able to resume where it left off.

### Conflict resolution



### Metadata

Storing metadata along with data for later (perhaps automated) deposit in a repository is a core research data management practice. If a dedicated "Academic Dropbox" tool was created, it may be possible to 

## Existing solutions that might work

### Unison

http://www.cis.upenn.edu/~bcpierce/unison/

#### Pros

* Excellent handling of conflicts (choose which copy to use, or merge the two where possible)
* Allows synchronisation of arbitrary pairs of folders, so will work with any storage that can be mounted by the user
* Gracefully handles interruptions of the transfer, and restarts next time from where it left off
* Uses the rsync protocol to transfer only the parts of files which have changed
* Can transfer files over an encrypted SSH connection

#### Cons

* Requires initial configuration by the user: in Mac or Linux this can only be done by editing configuration files, though the Windows client has a 
* Needs to be explicitly run by the user, which is easy to forget; could be run on a schedule, but this typically requires
* For large sets of files, scanning for changes can take a long time, particularly over the network

### Rsync

http://rsync.samba.org/

#### Pros

* Allows synchronisation of arbitrary pairs of folders, so will work with any storage that can be mounted by the user
* Very flexible, and operates without user interaction, so can be adapted to fit many situations
* Uses the rsync protocol to transfer only the parts of files which have changed
* Can transfer files over an encrypted SSH connection

#### Cons

* Syncs in one direction only, so full synchronisation requires two runs, one in each direction
* Command line tool has many complex options, and the available GUIs only go a small way to improve this, so it can be difficult for non-technical users to understand

### SparkleShare

http://sparkleshare.org/

* Works a lot like Dropbox
* (Currently) requires a Git repository
* Could potentially build alternative backends

### Git-annex

http://git-annex.branchable.com/

### Sharebox

https://github.com/chmduquesne/sharebox-fs

### Git-bigfiles

http://caca.zoy.org/wiki/git-bigfiles

### git-media

https://github.com/schacon/git-media

### Boar

https://code.google.com/p/boar/

### Mercurial large files extension

http://mercurial.selenic.com/wiki/LargefilesExtension

### Oxygen Cloud

https://oxygencloud.com/

* Commercial offering

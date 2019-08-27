# Install winrar on CentOS 6.x
Steps to install WinRar on Cent Os machine in order to un-rar a rar archive transferred from windows machine.

Fazer o Download dos links:
 - For Linux – i386:  http://www.rarlab.com/rar/rarlinux-4.2.0.tar.gz
 - For Linux – x64:  http://www.rarlab.com/rar/rarlinux-x64-4.2.0.tar.gz

## Step 1  – Download the winrar package
– move to the directory you want to save the downloaded package to.

– then enter the following command:

[user@localhost]# wget http://www.rarlab.com/rar/rarlinux-x64-4.2.0.tar.gz

    Sample Output
    [root@localhost root]# wget http://www.rarlab.com/rar/rarlinux-x64-4.2.0.tar.gz
    –2012-09-05 06:31:32– http://www.rarlab.com/rar/rarlinux-x64-4.2.0.tar.gz
    Resolving www.rarlab.com… 217.70.129.242
    Connecting to www.rarlab.com|217.70.129.242|:80… connected.
    HTTP request sent, awaiting response… 200 OK
    Length: 979938 (957K) [application/x-gzip]
    Saving to: ârarlinux-x64-4.2.0.tar.gzâ

    100%[==========================================================

    ===============================================================

    ===============================================================

    ===========>] 979,938 270K/s in 3.9s

    2012-09-05 06:31:41 (248 KB/s) – ârarlinux-x64-4.2.0.tar.gzâ

 

## Step 2  – untar the package
enter command:  # tar -xvf rarlinux-x64-4.2.0.tar.gz

    Example
    [root@localhost root]# tar -xvf rarlinux-x64-4.2.0.tar.gz
    rar/
    rar/technote.txt
    rar/order.htm
    rar/acknow.txt
    rar/readme.txt
    rar/rar_static
    rar/default.sfx
    rar/license.txt
    rar/rarfiles.lst
    rar/whatsnew.txt
    rar/makefile
    rar/rar
    rar/unrar
    rar/rar.txt
 

## Step 3 – Copy Rar and Unrar to /user/sbin
    [root@localhost root]# cd rar
    [root@localhost rar]# ls
    acknow.txt license.txt order.htm rarfiles.lst rar.txt technote.txt whatsnew.txt
    default.sfx makefile rar rar_static readme.txt unrar
    [root@localhost rar]# cp rar unrar /usr/bin

 

## Step 4 – Usage
    to unrar a file:   unrar x filename

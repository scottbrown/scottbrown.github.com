---
layout: default
title: My Client Development Setup
published: true
---

Virtual machine technology has been a boon to consultants like myself
who work with multiple clients.  I use 
[VirtualBox][ref-1] (it's free and 
robust) on a Windows 7 host.  When I work with different clients,
I need to use different skill sets: PHP, Ruby, Postgres, MySQL, Nginx,
Apache, you name it.

Each of these types of technologies can be contained within a single
machine, but I find that there can be some bleed between different
clients' installation needs.  Let's look at two scenarios.

Scenario 1
----------

Client A requires Rails 2.3 with various gems, whereas Client B requires
Rails 3.  This is possible with [RVM][ref-2] if 
your clients require different
versions of Ruby, but if each client requires the same version of Ruby 
you need to be sneaky and install a specific patch level for the same
Ruby version.  Once both patch levels are installed, you can use the RVM
alias command to name each patch level to each client's name.

    $ rvm install ruby-1.9.2-p100
    $ rvm install ruby-1.9.2-p101
    $ rvm alias create clientA ruby-1.9.2-p100
    $ rvm alias create clientB ruby-1.9.2-p101

The problem with this approach is that it is quite dangerous to cherry
pick specific patch level for Ruby versions.  In addition, you cannot 
upgrade to the latest Ruby version patch level.

Scenario 2
----------

Client A and Client B are very paranoid about network security.  In 
order to access both clients network, you need to install and run all
network traffic over a VPN connection.  The way VPN works, once you
route network packets over one VPN server, you cannot start another
VPN connection over top of it ( in a simple world, this is true.  I 
realize that over multiple NICs this is not a problem ).

The Solution
------------

If there is one thing I love, it's organization and simplicity.  When I 
take on a new client, I create a new VirtualBox environment for them.
Since most of my consultant work is software development, the client usually doesn't
care which operating system I use, so I choose Ubuntu.  I keep an ISO
image of the latest Ubuntu version handy on my Windows 7 host so that I
can create VMs on a whim.

Maintaining all of these VMs does take considerable disk space, CPU, and
RAM which is why I have use a desktop workstation in my office with a dedicated
1TB drive.  My host computer is Windows 7 simply because I can jump into 
a Windows application should it be required (which is rare, but necessary).  I
give each VM a 32GB disk, which should be more than sufficient for everyday
client tasks.

In my existing system, I have an Intel Core i7 with 4 cores, running at approx.
2.9Ghz.  Add to that 12GB of RAM and I can run about 4 VMs smoothly (assuming
each VM requires only 2GB of RAM, which is typically sufficient).  

If one client requires more RAM, it is a simple change for me:
1. Shutdown the VM
2. Change the VM guest config to increase the RAM
3. Start the VM

If a client requires me to process a large amount of data (e.g.: 1GB/day Apache
access logs), there are a couple
more steps to the upgrade, but it's still an easy task.  The problem with Linux
VMs (at the moment) is that they can't take advantage of an expanding disk (unlike
Windows whose VM disk will grow to meet the needs of the guest).  The trick is to 
add a secondary "hard drive" to the Linux VM and mount it like you would a normal
hard drive.
1. Shutdown the VM
2. Add a new virtual hard disk
3. Walk through the hard disk creation steps (this is similar to when the VM was
first created).
4. Start the VM
5. Mount the new hard disk (it should show up as a new hard drive.

Notes For The Future
--------------------

I need to learn how to script VirtualBox so that I can simply run a shell
script to prepare for a new client.

[ref-1]: http://www.virtualbox.org/  "VirtualBox"
[ref-2]: http://www.beginrescueend.com/ "RVM"


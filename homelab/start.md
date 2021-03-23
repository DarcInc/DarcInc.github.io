# Homelab
Present circumstances in 2020 and early 2021 aside, we've been hearing more about peoples' homelab setups.
I want to add my voice to the mix in the hope that people find this useful.
As I go on the journey of building out my own homelab, I'd like to share what learned.
I thought I'd start this, even if it winds up just being a list of links to better tutorials.

## What's a Homelab?
I look at a home lab as a stable layer of infrastructure, indepndent from your work or personal system, used for learning or experimentation.
Let's take that apart for a minute.
Even in the most chatoic of home labs there is still some level of structure.
For example, the space might be set up to provide networking and power to a bench.
The networking and power need to be there for the actual learning and experimentation, and aren't rebuilt on a regular basis.

## A Homelab Has a Purpose
Not everyone is interested in the same things.
For example, a data scientist and a hardware hacker have different needs.
The data scientist may need a stable platform on which to install and run tools.
The tools and scripts are changing but the actual computers probably aren't ever opened.
The hardware hacker is going to stick logic probes into things and twiddle power.
Parts of things are being assembled, reassembled and desoldered.

The purpose of my homelab is to experiment with automation.
I'm primarily intersted in how to take a pile of computers and turn it into something useful without human intervention.

1. I need some hardware - but I'm really not too picky.
    I'd like it to be the same.
2. I need a network - a single switch should be fine.
    Two switches - if I want separate storage or control-plane networks.
3. It should be easy to re-provision the OS disks - to get back to that "start from sratch" point.
4. There should be some kind of mass storaage.
5. The compute nodes should have sufficient capability to run "reasonable" software.
6. It can't take up too much space or require too much power.
    This is going into my home office.

### How I'm Meeting My Needs
I've settled on Raspberry Pis.
The 3B+ and 4B can be powered over ethernet with the POE hat.
The boot O/S sits on one micro SD card, which I can quickly re-flash.
For an OS I'm using FreeBSD.
FreeBSD is grok-able by one brain and comes with the batteries I need.
For power and networking I'm using power-over-ethernet.
And for mass-storage I'm taking this opportunity to switch to a new NAS and re-puprpose my old Synology NAS as NFS shares and iSCSI targets.

### Possible Shortcomings
AMD 64 support for FreeBSD is great but the ARM 64 is a little spotty.
For example, I don't think the POE fan will turn on and the CPU may not be frequency scaling.
It's harder to build a system with ZFS because of memory constraints and a lack of a proper disk interface.
The disks on the Synology are 5+ years old.
There is "interesting" software I can't run because of system constraints.
Linux and kubernetes is where much of the industry "is at" and has better support for the ARM 64 platform.

All these are manageable.
I don't need crazy compute performance.
Even though the fan doesn't work, the Pis stay within 65 degrees C when performing heavy compute tasks.
I can do some ZFS testing with the iSCSI luns.
I am really focused on software such as NGiNX, PHP, Node, Ruby, Postgres, and MySQL.
All these are avilable.
I think FreeBSD jails are better suited to automation on small clusters.

## A Homelab Is Not Dogfood
If my experiments work out, I might start "dogfooding."
That's the process of using my own stuff for my purposes.
Say I'm able to provision databases and network servers with the push of a button.
I might use that same system to stage this blog before shooting it up to GitHub.
Or I might start a project to build an app.
That's another infrastructure I would build out so I can still tear down and rebuild the homelab.


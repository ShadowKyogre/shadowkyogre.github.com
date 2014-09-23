<!-- 
.. title: My Experiences with ninit [Part 1]
.. slug: my-experiences-with-ninit-part-1
.. date: 2014-09-18 06:13:15 UTC-07:00
.. tags: ninit,systemd,eudev
.. link: 
.. description: 
.. type: text
-->

This post is a collection of notes of the process I went through to take out systemd for ninit. Pardon for the scarcity, but I'll revisit this with better descriptions.
# What IS ninit?
# Preparation
0. Install procps-ng-nosystemd
1. Temporary symlink to systemd-udevd
2. Install ninit
3. Set up service directories. You can find a rough copy (though not perfectly synced) copy of my /etc/ninit dir [here](github.com/shadowkyogre/ninit-boot)
4. Reboot

# Post-install
## eudev{,-systemdcompat}
1. manually build eudev and eudev-systemdcompat
2. Remove the symlink from preparations in systemd
3. intall eudev and eudev-systemdcompat
4. Reboot to test things

## nsvc -o {halt,reboot} vs ninit-shutdown -{o,r}
I recommend ninit-shutdown -{o,r} if you don't want to manually handle turning services off before
doing shutdown preparations. ninit-shutdown also assumes quite a few things about how a system should
be cleaned up, so if you want more control, you're going to have to create a service to manually shutdown
the services you want in the correct order before halting.

## Optional: pretty messages for every section started

## Depends aren't really "depends" - more like "start before"
Title says it all. ninit won't actually check if the services that a service depends on have finished executing with success or are running.
Some ways to work around this include:
* Specify the order daemons are started in like /etc/rc.conf, except with /etc/ninit/daemon/depends: Simple enough work around. 
Everything's also started in parallel like this.
* Patch ninit to include a separate file for services (opt) that specifies true deps that're only run once OR modifies the depends of certain services
once it's done running: Too complex, but could be done.
* Use setup, rsetup, or sys-rsetup to do the dependency checking for shared dependencies: One of the things that the ninit docs **don't** tell you 
is that using nsvc as a synced or waited service is NOT a good idea (nor as a services that's in depends either). I really wouldn't recommend this because this makes things complex.

# Thoughts
ninit's good enough if you've got a static configuration that doesn't have too many depends that can be easily manually managed. It also doesn't seem to
keep track of exit codes for error spotting (since a service could fail, but report back as finished).  For true depends, I'd recommend something else 
(at least until I can figure out how to patch the run helper in ninit to work around this). I'm thinking of maybe also trying out busybox init+(monit or perp), 
initng, OpenRC, or initscripts-fork. Currently, I'm interested in trying monit (even though this'd probably be a little too big for my own needs) since 
it does this dependency checking on its own and provides some additional security features that can be coded (eg: stop running a compromised service). 
The only thing that scares me about it is that it prefers pid files instead of being a direct parent of the process (as evidenced by with matching|pidfile when
asking what to check for a pid). I just need to figure out which init system to run it from before I start trying it out.

# Resources
* <http://www.linuxfromscratch.org/pipermail/blfs-support/2004-March/049009.html>
* <https://github.com/ShadowKyogre/ninit-boot>
* <https://github.com/ShadowKyogre/systemd-unit-converter>

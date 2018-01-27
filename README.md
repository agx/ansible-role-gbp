ansible-role-gbp
=================

Install gbp and pbuilder+cowbuilder to build Debian packages from git. Create
the chroots needed to perform builds therein.

Requirements
------------

A Debian based distribution.

Role Variables
--------------
The chroots wanted chroots are specified via the *gbp_cowbuilder_targets* dictioary:

  gbp_cowbuilder_targets:
        - dist: buster
        - dist: stretch
        - dist: buster
          arch: armhf
          foreign: true

Would create Debian buster and Debian stretch chroots for the host architcture
as well a buster chroot for armhf using qemu-deboostrap since this is marked as
a foreign architecture (a architecture using a command set that can't be run by
the host architecture).

Dependencies
------------

None known.

Example Playbook
----------------
The build host is assumed to run amd64 and we create chroots for amd64, i386
and armhf:

    - hosts: servers
      roles:
         - role: gbp
           gbp_cowbuilder_targets:
             - dist: buster
             - dist: buster
               arch: i386
             - dist: buster
               arch: armhf
               foreign: true

License
-------

GPLv3+

Author Information
------------------

Author: Guido Günther <agx@sigxcu.org>

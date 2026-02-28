.. helloWorld documentation master file, created by
   sphinx-quickstart on Fri Jul 17 10:38:59 2020.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.

Michael Alfield's Eco-Libre Volunteer Test
==========================================

.. toctree::
   :maxdepth: 2
   :caption: Contents:

This documentation is the final deliverable of the Eco-Libre Volunteer Test, preformed by Michael Altfield.

.. figure:: /eco-libre-volunteer-test2.jpg
  :align: center

  Screenshot of the FreeCAD object with my initials carved into them, as required by the Eco-Libre Volunteer Test

The purpose of this test is to demonstrate experience with all of the tools necessary to be successful as a volunteer with Eco-Libre. These tools include: GNU/Linux, git, FreeCAD, recordmydesktop, kdenlive, and PeerTube. The test also demonstrates a familiarity with open-source licensing, specifically the `Creative Commons Attribution-ShareAlike 4.0 International <https://creativecommons.org/licenses/by-sa/4.0/>`_ license, under which all of Eco-Libre's works are licensed.

Other key tools that are necessary for volunteering with Eco-Libre, but were not included in this test for brevity and simplicity, include inkscape, gimp, audacity, wordpress, and mediawiki.

Please see the video below showing how I carved my initials into the sheet of metal in FreeCAD.

.. raw:: html

        <iframe title="Michael Altfield's Eco-Libre Volunteer Test (2026.02)" width="560" height="315" src="https://peertube.linuxrocks.online/videos/embed/50d9585c-a912-4b1d-94c9-b7a09a456187" frameborder="0" allowfullscreen="" sandbox="allow-same-origin allow-scripts allow-popups allow-forms"></iframe>

Pain Points
-----------

This section will document the issues I had with completing the Eco-Libre Volunteer Test. I'm writing this to help the next person, who can review prior volunteers' tests for guidance.

Linux
^^^^^

I had some issues installing Linux as an HVM on my system running Qubes. First I used Linux Mint, but then I found that ``freecad`` is not available in the apt repos.

I spent some time researching alternative Linux Distros that are based on Debian and default to xfce. I'm not sure if all of these satisfy these two requirements, but initial searching suggested MX Linux, Peppermint Linux, Xubuntu, Linux Lite, Void Linux, and ExTiX Linux.

After considering these options, I decided to ditch xfce when I found-out that cinnamon was created after the gnome UI changes in v3. I read that cinnamon was similar to xfce.

**I decided to use Linux Mint Debian Edition (LMDE)** because it has a huge user base, lots of video tutorials online (which would help future Eco-Libre volunteers using linux for the first time), it's Debian-based (so it has ``freecad`` in its default repos), and it uses Cinnamon DE by default (so it should be lightweight and fairly easy to use for first-time Linux users).

Installing LMDE failed on the first time, because Qubes gives it three disks, and I didn't know which disks to use. I wanted to use an HVM, so the private storage disk was irrelevant. I set the system storage disk to 40 GB, and I installed the OS on that (/dev/xvda). The problem was that, after configuring the partition layout, it defaulted to installing the (grub?) bootloader on /dev/xvdb. And then, after the reboot after the install, the system failed to boot. The fix was to install both the OS *and* grub to /dev/xvda. This isn't going to be an issue for others, as it's a complexity created by Qubes. Most users will probably just have 1 physical disk on their computer, so installing LMDE will be easier.

Sphinx
^^^^^^

I had some issues getting this sphinx documentation site to build in GitHub.

I started by copying all of the files from `this repo <https://github.com/maltfield/rtd-github-pages>`_, as described in `this article <https://tech.michaelaltfield.net/2020/07/18/sphinx-rtd-github-pages-1/>`_

I had a permissions issue on the CI workflow, which tried to create a new 'gh-pages' branch and push to it. This is because GitHub changed the UI/process required to get the CI to run properly. The solution was described in `commit a07329b76d7017cc5171ddf321deec0b148f4bbb <https://github.com/maltfield/eco-libre-volunteer-test/commit/a07329b76d7017cc5171ddf321deec0b148f4bbb>`_

::

   I attempted to fix this from the GitHub WUI by going to:
   
   Repo -> Settings -> Actions -> General -> Workflow permissions
   
   * https://github.com/maltfield/eco-libre-volunteer-test/settings/actions
   
   On that page, I changed it from "Read repository contents and
   packages permissions" to "Read and write permissions"

After the GitHub CI container had permissions, the site failed to redirect because `GitHub changed 'master' to 'main' <https://github.com/github/renaming>`_, so I `had to change <https://github.com/maltfield/eco-libre-volunteer-test/commit/eca22a0a76a21f1202490b6b643bbcd768860663>`_ the script to say ``main`` instead of ``master``.

I then had some trouble embedding the PeerTube video. I wanted to use an existing open-source directive, but both of them were broken for different reasons (see `commit history <https://github.com/maltfield/eco-libre-volunteer-test/commits/main/?since=2026-02-27&until=2026-02-27>`_ for more details). In the end, I just settled by passing the "embed" code into a `raw directive <https://docutils.sourceforge.io/docs/ref/rst/directives.html#raw-data-pass-through>`_.

These issues should not be problems for subsequent users, as the intention of me doing this test is so that future volunteers can simply clone `this git repo <https://github.com/maltfield/eco-libre-volunteer-test/>`_, which has already solved *most* of these problems (though permissions issues in GitHub, as described above, may change again in the future).

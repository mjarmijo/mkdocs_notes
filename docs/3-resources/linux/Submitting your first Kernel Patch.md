[[Linux]]
[[Kernel]]

https://kernelnewbies.org/FirstKernelPatch

This tutorial will cover how to get your first patch submitted. You have three choices for how to complete this tutorial:

    Run Linux in VMPlayer from Windows.
    Run Linux natively on your own machine.
    Run Linux within VMPlayer on Linux. 

We recommend running Linux natively. Most Linux kernel developers run Linux natively, so you may as well get used to it. :) If you want to run Linux in VMPlayer, follow these directions. Note, you will not be able to compile the Linux kernel on a Mac, because the filesystem defaults to case-insensitive.

This tutorial assumes you are running Ubuntu or Debian. If you are running Fedora, Suse, Arch, or Gentoo, the package installation commands or package names may be slightly different. Ask for help on #kernelnewbies on irc.oftc.net if you get stuck. If (and only if) you are an applicant for Outreachy, then you should ask for help on #kernel-outreachy on irc.oftc.net.

Additionally, we highly recommend that applicants have a stable internet connection, with no download caps. Communication over IRC can be difficult if your internet connection keeps dropping or has a big lag time, so you need a stable internet connection. Downloading the initial kernel will use over 5 GB of data, which will easily blow through a standard 3G capped plan. We recommend making sure you have cable internet, or an unlimited 3G plan. 
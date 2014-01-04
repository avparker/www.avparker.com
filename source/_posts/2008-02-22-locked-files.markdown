---
layout: post
title: Deleting locked files from a USB drive in OS X
categories:
- mac
- misc
comments: true
---
I ran into the following dialog when trying to "Empty Trash" in OS X (10.4)

{% avpimgcenter /wp-content/uploads/2008/02/trash-locked-files.png 404 'the operation cannot be completed' %}

The problem was caused by a couple of hundred _locked files_ on the USB drive, which OS X happily sent to the trash but would not let me delete. Normally you can just restore a file from the Trash to a normal file, and then alter the properties (File -> Get Info in the Finder). But since the files were on a USB drive I couldn't see them in the Trash.
So the files were effectively stuck, and I couldn't empty the Trash without hitting "continue" a _couple of hundred times_ (and the locked files would still be there, so that would happen every time).

After a quick google, and a look at <code>man chflags</code>, I found a solution. Open terminal, and run the following commands (replacing <code>YOUR-DRIVE-NAME</code> with the volume name of your USB drive). __NOTE: run the following command at your own risk!__

<pre><code>
find /Volumes/YOUR-DRIVE-NAME/.Trashes -type f -exec chflags nouchg {} \; -print
</code></pre>

After than, "Empty Trash" worked as normal.

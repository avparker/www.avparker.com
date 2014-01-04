---
layout: post
title: "Reading Kanji on the Web"
date: 2005-04-11 17:27
categories:
- japanese
comments: true
---
[Tinyapps](http://www.tinyapps.org) has [a post](http://www.tinyapps.org/blog/2005_04_01_archive.html#111317947814308767) (complete with some nice screenshots) discussing the use of [jBrowse](http://www.jbrowse.com/products/jbrowse/), which augments a web page with "furigana" (Kanji with the hiragana reading above it). While it's a great idea, it's a plugin that is only available for Internet Explorer ([firefox](http://www.getfirefox.com/) and [safari](http://www.apple.com/safari/) are both superior).

[rikai.com](http://www.rikai.com/perl/Home.pl) is a great alternative that uses javascript to augment a site, displaying the *readings and meanings* of Kanji (including compounds, and some katakana words) when you mouse over the page. Just enter the URL into the box near the top of the page, and hit *Go*.

For example, given the following text:
<div style="text-align:center;">
2年前から日本語をべんきょうしています。
私の日本語はまだ下手ですががんばています！
(For the last 2 years I’ve been studying Japanese.
My Japanese is still poor, but I’m sticking with it!)
</div>

The [augmented version of this page](http://www.rikai.com/perl/LangMediator.En.pl?mediate_uri=http%3A%2F%2Fwww.avparker.com%2F2005%2F04%2F11%2Freading-kanji-on-the-web%2F) will look like
{% avpimgcenter /wp-content/rikaihover.png example of rikai.com augmentation %}

**Notes**

- You can also enter Japanese text directly into the box for a translation.
- If you enter a URL, make sure it is the only thing in the box, otherwise it will be interpreted as text (see above point).
This includes empty lines (i.e. don't put in the link and press &lt;Enter&gt;)
- The augmented page has some advertising at the top
- It doesn't seem to work when the *URL* contains japanese.
For example, my blog entry [こんにちは！](/2005/04/02/%E3%81%93%E3%82%93%E3%81%AB%E3%81%A1%E3%81%AF%EF%BC%81/) doesn't work.

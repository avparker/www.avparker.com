---
layout: post
title: iTunes/gmail dynamic counters...
categories:
- development
- software
comments: true
---
[Michael](http://www.softwareas.com) has an explanation of [how the itunes sale counter works](http://www.softwareas.com/ajaxian-guesstimate-on-download-counter) using [AJAX](http://www.ajaxpatterns.org). This reminded me of the storage space count on the [gmail](http://gmail.google.com) page (if you have an account on gmail you may not see the dynamic counter unless you logout).

I won't give a full walkthrough, as I've only spent about 30 seconds looking at the code. But the gmail counter is a bit simpler than the apple version, probably due to the fact that google completely control the rate of growth. This allows them to rely only on static data served with the page (they've scheduled/estimated the amount of storage that will be available at some times in the future), and then they simply use linear interpolation based on the current time.

For example, my page was served with the static data defining the [time, capacity] pairs:
{% codeblock lang:javascript %}
    var CP = [
         [ 1117609200000, 2250 ],
         [ 1120201200000, 2350 ],
         [ 1122879600000, 2450 ]
    ];
{% endcodeblock %}
For the curious, these entries correspond to the start of June, July and August respectively. I expect as it approaches August, they will start serving pages with an entry for September.

The update code simply finds the relevant entry in the <code>CP</code> array, and then interpolates based on the current time.

{% codeblock lang:javascript %}
    function updateQuota() { 
      if (!quota) {
        return;
      }
     
      var now = (new Date()).getTime(); 
      var i;
      for (i = 0; i < CP.length; i++) {
        if (now < CP[i][0]) {
          break;
        }
      }
      if (i == 0) {
        setTimeout(updateQuota, 1000); 
      } else if (i == CP.length) {
        quota.innerHTML = 'Over ' + CP[i - 1][1];
      } else {
        var ts = CP[i - 1][0];
        var bs = CP[i - 1][1];
        quota.innerHTML = format(((now-ts) / (CP[i][0]-ts) * (CP[i][1]-bs)) + bs); 
        setTimeout(updateQuota, 1000); 
      } 
    } 
{% endcodeblock %}

This is a good illustration how _precomputation can avoid trips to the server_.
Although, since it doesn't use a roundtrip, I guess it doesn't count as AJAX at all...

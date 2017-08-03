iOS Redirection Page
==============

With iOS 10.3, Apple has has introduced another redirection mechanism that developers must handle when attempting to implement mobile deep-link routing.
At some point in early 2017, a few enterprising scammers figured out how to hijack iOS Safari by abusing the custom URI scheme confirmation alert. 
This alert prevented user interaction until it was dismissed; so, the result of triggering it in an endless loop was essentially low-tech ransomware. 
Unfortunately, it was realistic enough to trick many users into paying up. In iOS 10.3, Apple fixed this security hole by changing the confirmation alert into a new non-blocking dialog.

![iOS Safari Open App Store](/1-Safari-Modal-Open-App-Store-opt.png)
Format: ![Alt Text](url)

However, there are actually two problems:

* It’s an extra step.
Users don’t like extra steps, especially because downloading a new app is already relatively high-friction. 
Adding another tap certainly doesn’t help.

* Users can press “Cancel.”
This is the much bigger problem. Pressing “Cancel” can leave users trapped on an empty page in Safari. Even worse, if they’ve come from another app and then go back to click the same link again, it’ll show this error message and do nothing:

![iOS Safari Error Message](/2-Safari-Modal-Error-Message-opt.png)
Format: ![Alt Text](url)


### This is how you fix the iOS 10.3 redirection issue

You can’t avoid the alert dialog. And the reality is that some users will click “Cancel,” either on purpose or by mistake.
What you need to do is to build a download app screen. This will be a simple page with a download link to the iTunes store.

The key part of this is the JavaScript at the end:

```
<script type="text/javascript">
	window.onload = function() {
		window.location = "<% iTunes Store URL %>";
	};
</script>
```
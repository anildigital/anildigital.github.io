--- 
wordpress_id: 302
title: Using OpenID delegation
wordpress_url: http://anilwadghule.com/blog/?p=302
layout: post
---
<p style="text-align: justify;">I am using OpenID (<a href="http://claimid.com/anildigital">http://claimid.com/anildigital</a>) for quite sometime.
I am aware of benefits of using OpenID for logging in to different OpenID supported sites.

<p style="text-align: justify;">But I always had question, how OpenID solves the problem of multiple login ids.
Suppose today you like <a href="http://claimid.com">http://claimid.com</a> as OpenID provider,
tomorrow you might like different OpenID provider. So if you create a new OpenID,
you will use this new OpenID to logging in to OpenID enabled sites.
Then what about previously using OpenID, what about all previous accounts created with it.

<p style="text-align: left;">For all your previous accounts, if you want to keep the same account on site, you
need to login with your old OpenID, . If you try to use new one, it will be treated as
new OpenID and new account to the site. So finally using OpenIDs results into using
multiple OpenIDs. That's why, I was really not impressed with OpenID concept.

<p style="text-align: left;">But today, I came to know about this great concept, OpenID delegation.
Its very simple and clean concept. What is it?
<blockquote style="text-align: left;">Delegation allows you to use your own website as your identifier while
still using a third-party OpenID provider. This requires only the
ability to add a small snippet of HTML code to the page you wish to
use as your identifier.</blockquote>
<p style="text-align: left;">So you can use your own website address as OpenID, in my case it is anilwadghule.com.
You could setup delegation with any of OpenIDs. You could keep changing your OpenID
from OpenID providers and just use your site address as delegated OpenID.

<p style="text-align: left;">You need to add following code to your sites index.html or any index page, which gets
rendered when you hit yoursite.com
<pre class="terminal"><code>
&lt;link rel="openid.server" href="https://www.myopenid.com/server"&gt;
&lt;link rel="openid.delegate" href="http://anildigital.myopenid.com"&gt;
</code></pre>
<p style="text-align: left;">Now you can use your website address as your OpenID. Thats it.
In my case it is <a href="http://anilwadghule.com">anilwadghule.com</a>

<p style="text-align: left;">Now you don't want myOpenID as OpenID provider and you think claimid.com is better OpenID
provider just replace above snippet with code
<pre class="terminal"><code>
&lt;link rel="openid.server" href="http://openid.claimid.com/server" /&gt;
&lt;link rel="openid.delegate" href="http://openid.claimid.com/anildigital" /&gt;
</code></pre>
<p style="text-align: left;">And now you can still use your delegated OpenID to login to different OpenID enabled
websites.
<p style="text-align: left;">Awesome right?. So go start using your website address as OpenID!</p>

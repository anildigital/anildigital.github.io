--- 
wordpress_id: 251
title: test/spec 0.4 released!
wordpress_url: http://anilwadghule.com/blog/2007/06/30/testspec-04-released/
layout: post
---
<a href="http://chneukirchen.org/blog/archive/2007/06/announcing-test-spec-0-4-a-bdd-interface-for-test-unit.html">test/spec</a> is BDD interface for Test::Unit. I got chance to use it for <a href="http://taskbin.com">TaskBin</a>.
I found that writing tests using BDD is more fun than Test::Unit tests.
Check <a href="http://chneukirchen.org/blog/archive/2007/01/announcing-test-spec-0-3-a-bdd-interface-for-test-unit.html">this link</a> for detailed test/spec explanation which was an announcement for test/spec 0.3.

BDD is the way of writing code by testing what the code should do, rather than testing the code itself. BDD = Behavior driven development.

Previously, I used to do TDD using Test::Unit which comes inbuilt with Ruby and fully supported in Rails.  Christian Neukirchen ( of <a href="http://anarchaia.org/">Anarchaia</a>  fame) wrote test/spec. Great work! I am very much excited to use test/spec further in my projects.

<a href="http://rspec.rubyforge.org/">RSpec</a> is also a very popular framework. But I have not explored it well and also, I wanted to do BDD, without losing/affecting my existing tests i.e. Test:Unit tests. That's why I chose test/spec, which allows me to write BDD tests without affecting my previous Test::Unit tests.

Following are some links which will help you to understand BDD in more detail.

<a href="http://errtheblog.com/post/4268" title="http://errtheblog.com/post/4268">http://errtheblog.com/post/4268</a> BE DEE DEE AND ME.

<a href="http://rspec.rubyforge.org/" title="http://rspec.rubyforge.org/">http://rspec.rubyforge.org/</a> Rspec site, detail explanation about using Rspec

<a href="http://lukeredpath.co.uk/2006/8/29/developing-a-rails-model-using-bdd-and-rspec-part-1" title="http://lukeredpath.co.uk/2006/8/29/developing-a-rails-model-using-bdd-and-rspec-part-1">Nice article</a> telling how to use BDD for rails model.

To install test/spec you just have to type
<pre>c:gem install test-spec</pre>
...on Windows
<pre>$sudo gem install test-spec</pre>
...on Linux and variants

and in your test_helper.rb or in your test file, add this line
<pre>require 'test/spec'</pre>
That's it, you can now write your BDDed tests in your old test files under unit/functional/integration tests.

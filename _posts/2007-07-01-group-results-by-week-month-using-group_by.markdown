--- 
wordpress_id: 252
title: Group results by week, month using group_by
wordpress_url: http://anilwadghule.com/blog/2007/07/01/group-results-by-week-month-using-group_by/
layout: post
---
I have a table named stats made up of two important columns 'stat_type' and 'count'. We run a rake task which populates <a href="http://taskbin.com">TaskBin</a> related statistics at the end of every day into the stats table. Column count holds count of users signed up per day is stored.

To generate the report, I fire the query from my controller action as
<pre>@stats = Stat.find(:all, :conditions =&gt; ["stat_type = 'signup_confirmed'"])</pre>
These model objects(@stats) are stored as per day basis. Now, I need to display the @stats grouped by month and grouped by week.
Rails enumerable class has a method called <a href="http://api.rubyonrails.com/classes/Enumerable.html#M001098">group_by</a> which is very super-powerful and allows us to group, active record objects by a passed parameter.

So here is the code which I wrote.

Add the following methods in model ( in Stat model),
<pre>def week
  self.created_at.strftime("%W")
end

def month
  self.created_at.strftime("%y%m")
end</pre>
Now just add following two magical lines in same controller action
<pre>#returns a hash, with key as week number and value as grouped results as array.
@weekly_stats = @stats.group_by(&amp;:week) 
@monthly_stats = @stats.group_by(&amp;:month)</pre>
(one point, use of &amp;: is dangerous as <a href="http://m.onkey.org/2007/6/30/let-s-start-with-wtf">pointed out by Pratik</a>, you can use @stats.map{|i| i.week} and @stats.map{|i| i.month } instead of &amp;: symbol.

And your view code will look similar like this (shown for week only).
<pre>&lt;% @weekly_stats.each do |week, stats| %&gt;
  &lt;tr&gt;
    &lt;td&gt;
      Week &lt;%= week %&gt;
    &lt;/td&gt;
    &lt;td&gt;
      &lt;% count_array = stats.collect{|i| i.count}%&gt;
      &lt;%= count_array.sum %&gt;
    &lt;/td&gt;
  &lt;tr&gt;
&lt;% end %&gt;</pre>
I hope you enjoyed this simple trick. Do comment if you have other tricks/suggestions.
Keep tasking. visit <a href="http://taskbin.com">TaskBin.com</a>.

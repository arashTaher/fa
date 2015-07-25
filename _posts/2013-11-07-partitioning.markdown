---
author: arashthr
comments: true
date: 2013-11-07 13:23:02+00:00
layout: post
slug: 'partitioning'
title: افراز‌
wordpress_id: 441
categories:
- Codes
- Fa
tags:
- Algorithm
- Pyhton
- Recursion
- Set
---

چند روز پیش در کتاب ریاضیات گسسته به مساله [افراز‌های یک مجموعه](http://mathworld.wolfram.com/SetPartition.html) بر خوردم. در کتاب به این موضوع اشاره‌ای نشده بود، اما کاملا مشخص بود که تولید این مجموعه از یک ساختار بازگشتی تبعیت می‌کنه.

از اونجایی‌ که موضوع پیچ و خم داری به نظر می‌رسید ( کافیه به فرمول یافتن تعداد اعضای این مجموعه نگاه بندازید تا بفهمید چی‌ میگم ) تصمیم گرفتم یک برننم برا تولید این مجموعه رو بنویسم.مسائل بازگشتی در حیطه مجموعه‌ها به صورت کلی‌ از قاعده "بودن و نبودن" پیروی می‌کنه. این یکی‌ هم استثنا نبود، هرچند کمی‌ ریزه کاری هم داشت.
خلاصه، این راه حلی‌ است که من برای این سوال پیش گرفتم، در زبان پایتون :


{% highlight python lineson %}
# Prints partitions of set : [1,2] -> [[1],[2]], [[1,2]]
def part(lst, current=[], final=[]):
    if len(lst) == 0 :
        if len(current) == 0:
            print (final)
        elif len(current) > 1:
            print ([current] + final)
    else :
        part(lst[1:], current + [lst[0]], final[:])
        part(lst[1:], current[:], final + [[lst[0]]])
{% endhighlight %}

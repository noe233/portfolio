---
layout: page
title: About
permalink: {{ site.baseurl }}/about
weight: 3
---

# **About Me**

Hi I am **{{ site.author.name }}** :wave:,<br>
I can chat in three human languages and code in quite a few computer
          ones. I'm on the path to becoming a Software Engineer, driven by a
          love for solving problems and always picking up new skills. I've
          wrapped up various tech projects and did an internship at a software
          development company. There, I got the hang of languages like
          Javascript and Python and learned my way around agile development
          methods. Want to know more about what I've been up to? Let's connect
          on LinkedIn. I'm keen to take on fresh challenges and keep growing as
          a software engineer. Looking forward to the journey ahead!.

<div class="row">
{% include about/skills.html title="Programming Skills" source=site.data.programming-skills %}
{% include about/skills.html title="Other Skills" source=site.data.other-skills %}
</div>

<div class="row">
{% include about/timeline.html %}
</div>

---
title: "This blog"
date: 2020-10-19T15:58:36+05:30
draft: false
tags: ["blog", "theme", "netlify"]
---

If you are wondering how I made this simple, yet elegant looking blog. It's quite simple.
I used [hugo](https://gohugo.io/) and a theme called [Archie](https://themes.gohugo.io/archie/).

You can find the code on my [git repo](https://github.com/rk2810/rohank.dev).

All I had to do was:

1. Link my git to [Netlify](https://www.netlify.com/).
2. Select my repo for deployment from a nice dropdown menu.
3. Buy a `.dev` domain from [Google Domains](https://domains.google/)
4. Add a custom domain for my app on Netlify.
5. After adding a custom domain, Netlify provides you with DNS info.
6. Add the Netlify provided DNS info in the DNS section of Google Domains panel. (That'll override the default DNS)
7. Netlify provides you with an SSL certificate by [Let's Encrypt](https://letsencrypt.org/), which I find amazing.
8. All caught up!

Hugo's documentation is very well written and maintained. There are a couple of themes to choose from.
The best part is, there is no vendor lock-in, I can literally move anytime from netlify to any other host with minimal effort.

The whole idea behind this blog was to provide some nifty tips I come across in my day to day life that might help my peers.
I am not doing this for views, my target audience is just the people who might find my work interesting. If you are reading this,
**you are indeed special to me**.

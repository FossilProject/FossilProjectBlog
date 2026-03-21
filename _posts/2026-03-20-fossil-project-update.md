---
layout: default
title: "Fossil Project Update — What's New and Where We're Going"
date: 2026-03-20
author: S.K. Ooma
---
# Fossil Project Update - What's New and Where we're Going

When I launched Fossil Project earlier this week with a single introductory post, the site was little more than a blog with a mission statement. A lot has changed since then, and I wanted to take a moment to document what's been built, why it was built, and where this project is headed.

---

## What's Live Right Now

**A FOSS news hub on the homepage**

The homepage now pulls live headlines from four major open source and Linux news sources. Currently Phoronix, LWN.net, OMG Ubuntu, and FOSS Post are what I have implemented as they are some of the bigger names of the news community. The goal is to make Fossil Project a single destination where you can catch up on what's happening in the FOSS world without spending too much time searching out the latest stories. More sources will be added over time.

**Our very own search engine!**

This one I'm particularly proud of. Fossil Project now has its own search engine built into the site, powered by a self-hosted SearXNG instance running on dedicated infrastructure. SearXNG is an open source metasearch engine that pulls results from Google, Bing, DuckDuckGo, Brave, and dozens of other sources at once, without tracking you, without profiling you, and without selling your queries to advertisers.

You can reach it from the search bar on the homepage or from any page on the site. Web, news, image, video, and tech filtered searches are all supported. The entire stack from the server to the frontend is built on open source software. I have plans to continue refining the engine and results we see from our engine as time goes on. My first goal was making it functional and secure outside of the SearXNG environment so that we could truly call it our own. That feels right for a site like this.

**A contact form, about page, and post archive**

The basics are in place. If you have a FOSS project you think deserves coverage, a question, or just want to reach out, the contact page is there. The posts archive organizes everything chronologically as the blog grows.

**Comments on every post**

Post discussions are powered by Giscus, which uses GitHub Discussions as its backend. No third party ad platforms, no tracking. If you have a GitHub account you can leave a comment. If you don't, that's worth thinking about as GitHub is where most of the open source world lives anyway.

---

## What's Coming

**A community forum**

A blog is a one way street. I want Fossil Project to be a place where people can actually talk to each other; where people can share projects, ask questions, debate which distro is worth switching to, and recommend FOSS tools they've found. A self-hosted forum is on the roadmap. The leading candidates right now are Discourse and Flarum, both of which are open source and self-hostable. Moderation is a real concern for a solo project, so this will be introduced carefully when the time is right rather than rushed out half-maintained.

**A FOSS games showcase**

One of the most overlooked corners of the open source world is its games. There are genuinely great games built entirely with open source tools and released under open licenses and almost nobody outside of dedicated communities knows they exist. Fossil Project will be adding a dedicated games section eventually with a curated list of notable FOSS games alongside browser-playable titles you can try directly on the site. No downloads, no installs, just open source games running in a browser. This section will also serve as a showcase for what's possible when developers build in the open.

**More weekly content**

The blog will cover a range of topics beyond game development, Linux tools, productivity software, privacy-respecting alternatives to mainstream apps, and spotlights on FOSS projects that deserve more attention than they get. If there's something specific you'd like to see covered, the contact form is open.

**Supporting Fossil Project**

Running a site like this has real costs. The search engine runs on a dedicated server, and keeping it fast, secure, and independent means paying for that infrastructure every month. Keeping ads off this site is a deliberate choice; the whole point of Fossil Project is to be a space that isn't trying to sell you something, but that means finding other ways to keep the lights on.

To that end I've set up a Ko-fi page for anyone who wants to help support the project. Ko-fi lets you make a one time donation or set up a small monthly contribution if you'd like to be a regular supporter. Every bit goes directly toward server costs and keeping Fossil Project ad-free and independent.

There's no pressure here. The site is free, the search engine is free, and everything built here will stay that way regardless. But if you've found something useful here and want to help it keep growing, it genuinely makes a difference.

You can find the Ko-fi page linked in the footer of the site when that is live.

---

## A Note on the Philosophy Here

Everything built into this site has been chosen on purpose and crafted with careful consideration. The search engine is self-hosted because your queries shouldn't be going to a corporate platform that will sell your data to some broker. The comments are GitHub-backed because I didn't want an ad network embedded in a site that talks about privacy. The main infrastructure runs on a real server because owning your stack matters.

This is all not for dramatic, hyperbolic intent. A site that talks about open source software should probably be built on open source software. Fossil Project is just trying to be consistent about that, one piece at a time.

More updates to follow both in terms of site upgrades and future blog posts in due time. Thanks for being here early.

*— S.K. Ooma*

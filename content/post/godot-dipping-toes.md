---
title: "Diving into Open Source: Dipping Toes in Godot"
date: 2018-05-04T10:35:04+05:30
---

# Introduction
Open Source Software is probably the greatest testament to Programmer culture, or at least, it is in my opinion.
You have a purely voluntary work experience on projects that you can't build alone - while simultaneously contributing to something
that more than you and your friends use. The feeling of your contribution to the world is a sweet feeling.

If you want to know more about open source [this should help](https://opensource.com/resources/what-open-source)

The reason why I'm writing this is as a newbie to Godot and someone who has been pushing his friends and college juniors into open source, I find that the greatest issue in starting Open Source Development is a sense of confusion about the starting points.
So I decided to list out the steps I took. These are specific to [Godot Engine](https://www.github.com/godotengine/godot)

### 1. Join the IRC

The most important thing in an Open Source project is the community. While Godot has a Discord and subreddits and all the rest, which is perfectly fine if you are just a user, but if you are serious about contributing, you should join the developers community -the developers IRC channel.
This allows you to interact with people who have been working on the project and comes in handy while bug fixing.

### 2. Clone the repository

So you’re serious about contributing. Amazing, next step, actually doing it. To start with you need the source code. How to set up everything? Well you just need to read this page on the PR workflow that Godot uses for work. As soon as your done with setup, build the engine. Instructions here.

### 3. Get an issue

There’s no sure shot way to know which issues you will be able to do. An easy check can be made by adding label:junior-job to your issues search panel, which will yield issues which are marked by the members as easy. This doesn’t mean they are cakewalk; it’s more of ‘doable by a newbie’ tag. Read the comments and the description properly, a lot of times hints are left by other developers on what has to be changed change or where and how to solve the issue. [This](https://github.com/godotengine/godot/issues/16684) was the first issue [I picked up](https://github.com/godotengine/godot/issues/16684#issuecomment-365612981).

### 4. Find problem

Finally, your chance to dive into the source. It’s not as simple as just searching for the fix and getting it.
Godot source code lacks and does not need comments since the code itself is self explanatory. At first it is a difficult job to find the part of the source code that you need. But as you keep working, instead of comments, you see exactly how the engine works and each issue leaves you with a lot more knowledge than before. Of course, you’ll need to navigate the source files to find what are the relevant files. (Tip: search keywords that are relevant; issue related to popup? Search for popup in the source code) Once you find a class that is involved in issue, track down the flow till you find the culprit. In my case, I was lucky that the [issue was already highlighted](https://github.com/godotengine/godot/issues/16684#issuecomment-365556856).

### 5. Fix Issue

Now all you have to do is write the fix (make sure it’s nice and clean.) Do a clang-format to make it adhere to the guidelines. Build the engine again and check if it works properly. If all well and done, pull with rebase (from upstream) followed by pushing to origin And then just go on github and [create a Pull Request](https://github.com/godotengine/godot/pull/16698). This might take some time and you might be told that there are better ways to do it or you need to correct something. Keep yourself updated with the thread of discussion and if you do change something just amend the commit to perfection.

### 6. Repeat

The point isn’t to solve just one issue (although even one issue is a good job), you have to keep repeatedly doing this, and over time you get used to the workings of the engine, and get faster and faster at solving problems be able to tackle more and more complex issues. 

# Conclusion

You don't need to be a omniscient programming god who can divine the fix for the most difficult issue. You can start by an issue as small as copy pasting the lines (seriously, check my PR). Despite being such an easy fix - it was left open for new developers. Most open source organizations do that for their juniors.

If you don't have an Open Source Organization that you want to contribute to - go contribute to Godot.

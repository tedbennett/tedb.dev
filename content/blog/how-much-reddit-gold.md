---
title: "How Much Reddit Gold?"
date: 2020-12-11T18:05:11Z
draft: true
description: "Add Two Numbers"
website: "www.howmuchreddit.gold"
github: "https://www.github.com/tedbennett/how-much-reddit-gold"
---

I recently saw a post on reddit asking how much premium another user would have received from a post they made with a lot of awards. I've seen a few websites around analysing some of the top reddit posts, but I hadn't seen one looking at individual posts, so I decided to make one.

The idea is that the user can paste in a reddit link, and get a visualisation of the rewards it has received.

I haven't used the reddit API before, but it turns out I didn't need to use it. Accessing the reddit post json gave me all of the info I needed - the post's name (obviously), subreddit, number of upvotes, etc. In addition, for each type of reward it received, it listed the reward count, how many coins it was worth, how much premium it rewarded, and a whole list of images at different sizes. 

The real kicker is that the json contains this information for *every comment response*. A post with quite a few rewards will definitely have a few comments with rewards. One post with quite a few upvotes, announcing Joe Biden winning the US Election, returns more than 70,000 lines of json, which takes the server more than 20s to respond (at least, when I was trying).

Once this was figured out, I put together a simple backend to extract the info needed. The front end is a simple React app using React-Bootstrap for styling. I tried to use React Hooks as much as possible, and used the `useContext()` hook to share data between child components.

I found the domain www.howmuchreddit.gold for only £5 which I was quite happy with, and deployed with Heroku.

As usual, I spent a whole lot of time figuring out some very minor components, in this case the little headers above the table. I still need to do a bit of work on the table and some minor things like number formats. The backend could do with a bit of work, and reddit's new app links currently don't work. 

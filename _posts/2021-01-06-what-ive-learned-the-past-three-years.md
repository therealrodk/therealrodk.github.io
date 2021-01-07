---
layout: post
title: What I've Learned The Past Three Years
postHero: /images/train-on-rails.jpg
author: THEREALRODK
postFooter: <a href="https://www.youtube.com/embed/hXNWa9E9vN8" target="_blank" rel="noopener">Cowboy Bebop OST</a>
---

### Where Ya Been?

Well, to be honest, I've been *busy.* And, since I haven't updated this blog in almost three years, I guess I'd better fill in the blanks.

### Letting Go

To begin with, I was hired immediately after my last post, so I did not have time to finish the Choctaw Dictionary Project I was working on. Which is alright, considering it turns out that a professor <a href="https://www.webonary.org/byington-choctaw/" target="_blank" rel="noopener">was also working on the same thing</a>. And his is finished.

### Moving On

<img class="pull-left" src="https://images.unsplash.com/photo-1509453721491-c3af5961df76?ixid=MXwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHw%3D&ixlib=rb-1.2.1&auto=format&fit=crop&w=2775&q=80" alt="Yellow hard hats" style="max-width: 300px;">

This gave me the chance to focus on my new job, which was for a company that makes training courses mainly for the construction industry. I had the opportunity to build an eCommerce site, a video training platform, and an internal coporate site, all in Rails, among other things.

The eCommerce site was actually more than just a custom eCommerce solution. The company's original site was a WordPress site, where customers purchased access to an LMS (learning management system), which was on a separate website. They had to then go to that website, create a separate account, and figure it out. It was fairly complex, and confusing to navigate.

The site I built took advantage of a third-party API provided by the LMS, which allowed me to build in the ability for managers to add employees easily, track their employees' progress, and quickly purchase and assign courses for them. Previously, this had to be done manually by office staff and took a bit of time. Accounts still had to be created for the LMS, but this was handled automatically on the new site, invisibly to the user, creating a seamless connection between the two.

The corporate site had two main features: a collection of common documentation, like an employee handbook and information on managing computer network safety, and a custom task manager, for tracking the creation of the aforementioned training courses.

The task manager was my favorite part of this site, because I had to find solutions for some problems. For one thing, multiple departments were involved with the creation of a training course. I wanted everyone to know at a glance what still needed to be done, and by whom. Several different training courses were under development at a time, so it was necessary to be able to scan the progress of multiple courses at once. I solved this by displaying a list of all training courses on the homepage, for logged-in employees. Each one showed a series of numbered circles representing each task that needed to be accomplished. The logged-in employee would see colored outlines around any unfinished tasks that belonged to their own department. Hovering over a circle would display the task name, and clicking on it would take you to a page for the task itself, for specifics.

Another part of this was that training courses would often have multiple different versions for different audiences, like Managers, Employees, and HR, for instance. The required tasks were usually the same, so in order to avoid users having to create these from scratch, and monotonously duplicate everything, I added the ability to clone training courses. The tasks for each training course, including those that had been cloned, could be viewed as a list and re-ordered via drag-and-drop, without affecting other courses.

This was a fun problem to solve and it was fulfilling to find a solution. The end result was much better than simply having things written on a whiteboard that was located in one office, where others could not see it, particularly at a time when people are frequently working from home.

### WordUp

<img class="pull-left" src="https://images.unsplash.com/photo-1584824486509-112e4181ff6b?ixid=MXwxMjA3fDB8MHxzZWFyY2h8Mnx8YnJva2VuJTIwY29tcHV0ZXJ8ZW58MHx8MHw%3D&ixlib=rb-1.2.1&auto=format&fit=crop&w=800&q=60" alt="Computer with 404 page" style="max-width: 300px;">

As the head of the web development department, I had three employees who worked under me. They were responsible for maintaining the company's WordPress website, with my guidance and assistance. Coming from a full-stack background, WordPress was occasionally frustrating, considering how easy it is to do certain things in Rails, like dynamically load information from a database, or make and use templates. It is also a challenge knowing that you have no control over the code in the plugins you use, and that they can potentially break everything else on your website with a minor update.

*The nightmare of having to turn off all of your plugins and re-enable them one-by one, in order to discover which one was causing an issue… Shudder…*

Thankfully, we found a third-party backup solution that also gave us a staging environment. Sadly, we learned that there is no easy way to merge updates, short of putting the site in maintenance mode (so no more orders could be placed). Otherwise, any new orders would be overwritten. Sometimes, documentation forgets to inform you of important things like this. *Sigh…*

### Backin' Up

<img class="pull-left" src="https://images.unsplash.com/photo-1562414962-a6b4f966070d?ixid=MXwxMjA3fDB8MHxzZWFyY2h8MTB8fGJhY2t1cHxlbnwwfHwwfA%3D%3D&ixlib=rb-1.2.1&auto=format&fit=crop&w=800&q=60" alt="A computer hard drive split in two" style="max-width: 300px;">

I was also responsible for maintaining the NAS (network attached storage) where all of our data was stored locally, including making sure everything was backed up off-site (ie, in the "cloud"). At first, we backed everything up to Amazon S3. This process was really easy, but took a *very* long time (most of a month, I think) to transfer a couple gigabytes of data to their servers. It also got pretty expensive, pretty quickly. Later, another developer introduced me to <a href="https://wasabi.com/" target="_blank" rel="noopener">Wasabi</a>. They claim to be 80% cheaper. They do not lie. Before leaving this company, I was able to get their backups migrated to Wasabi, and save them a lot of money.

### Letting GoRails

<img class="pull-left" src="https://d2i2nj5el4wq1j.cloudfront.net/assets/logo-a191a70fa781dc8b50cda97f97d8613b74079a5f7775ee51d78b06f4ee2fa9ac.svg" alt="The GoRails.com logo" style="max-width: 300px;">

During this time, I discovered the <a href="https://gorails.com/" target="_blank" rel="noopener">GoRails</a> website. This is an amazing resource! Chris, the guy who runs the site, is really talented, really kind, and always willing to offer advice on his associated Slack channel. The community is also fantastic, and there is always someone to lend an ear, or make suggestions for improving code or finding solutions. I highly recommend GoRails!

*Disclaimer: I am not an affiliate. Just happy to share a positive experience :)*

### Pig Tales

<img class="pull-left" src="https://porkbun.com/partners/logos/porkbun.comphpPkl2eU.svg" alt="The Porkbun.com logo" style="max-width: 300px;">

One other fantastic resource I discovered over these few years is <a href="https://porkbun.com" target="_blank" rel="noopener">Porkbun</a>. (*Again, not an affiliate…*) These guys are the easiest DNS I have ever used. I eventually was able to migrate all of our many domains names, save one, from the horrid GoDaddy to Porkbun, and never regretted it. This was no small feat, by the way, as GoDaddy's ever-changing requirements meant that it sometimes took _days_, literally, to migrate a single domain name. Bleh. Oh, and Porkbun's prices are some of the lowest I have ever seen, as well, which was nice.

### Final Thoughts

I have learned a lot over these past 2 1/2 years working for this company, which will make me an even better employee and developer wherever I go next. With 2020 behind us, here's to better days ahead!


<!--

Use this to place images within the article. Use the pull-left and pull-right classes for placement.

<img class="pull-left" src="http://placekitten.com/g/400/200"
     alt="kitten">
-->
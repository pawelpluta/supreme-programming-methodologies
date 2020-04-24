# Zero YOLO deployment

by @bslota

Nowadays, we are supposed to deliver new values to users without interrupting their work.
Constant rush for game-changing features that are using cutting-edge technologies might cause that some of developers 
are loosing their confidence when it takes to release a new version of the application. Changes become bigger and bigger, 
and you can never know, if a user will like it, or will hate it so much that it will be needed to revert the change. In extreme
situations, after a non-compatible change, the application even might be unusable due to performed changes!

To mitigate this risk, a proper methodology is needed. This abstract will help you to identify if you should try to 
implement this methodology in your team, will tell you, how to do it, and what are the benefits.

## Should I try it?

Before you will introduce a new methodology to a team, please keep an eye on your developers for a few days to check if their
behaviour reveals signs of a need for Zero YOLO deployment. Please use the following matrix that is describing behaviours and 
scores them. When a total count of points is over 6, you can consider introducing it. Any score above 9 means that you will
benefit a lot from this methodology, and you really should do it. You can even set it as your own, corporate personal goal
in your development plan.

Behaviour | Tips on identifying | Score
---|---|---
New and innovate technologies are being used | Developers are bragging about technologies that they are using. Carefully listen, what they are talking by the coffee machine and Google words that they emphasize | 1
Application is not tested automatically | Ask them "what is our code coverage?". If the percentage given is lower than your last year raise, you should add points for this behaviour | 2
Microservices or Cloud infrastructure is used | Listen for words like "Docker", "Kubernetes", "AWS", "Azure", "Container" or "Cloud" | 2
Frequent application releases | Check your mailbox for mails with a title like "Release notes". Ask team, if there is a page with release information. If releases are done on daily basics, add a point for this behaviour | 3
YOLO word is being used by the team before commit | Sneak near to the developers and hide so they cannot see you. Listen, if they shout "YOLO" and hit Enter key hard | 5
`git push -f` is used | Buy a cake and send an email that there is a free cake in the kitchen. Lured developers should leave their computers unattended. Look for those, that were not locked, quickly open terminal and browse command history for `git push -f` | 5

## I got over 9 points! Tell me, how to live?!

First of all, keep calm. Your developers might not even be aware of the problem. Discuss and implement the following steps with your team:
* expose health check of the application
* setup application monitoring
* create a pipeline for automatic building
* create a pipeline for automatic deployment
* create a pipeline for the creation of application infrastructure
* implement procedure for application rollback (take into account things like Database migration)
* place a jar that developers will put $5 every time that they will use "YOLO" word
* use a rolling update for deploying the application
* prepare instruction for introducing non-backwards compatible changes

There might be a lot of complaints at the beginning of transformation towards Zero YOLO deployment. Do not worry, 
developers are spoiled like a brat and do not like anything that will require additional effort to them. You can convince them by 
saying, that their value on the market will increase after implementing this methodology, and they can put it in their resume.

## Outcome

Through the tears and blood, you will gain confidence in deploying the application, possibility to quickly revert changes, 
users will become unaware of executing deployment and you will gain developers, that can brag themselves around with new
cool feature.

*you will also get rid of YOLO word*

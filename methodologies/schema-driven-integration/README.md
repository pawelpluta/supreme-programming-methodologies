# Schema Driven Integration

by [@bandrzejewski](https://github.com/bandrzejewski) & [@pawelpluta](https://github.com/pawelpluta)

Nowadays, systems are becoming more and more complex, therefore pursuit for simplicity has become a desirable alternative.
Even the biggest systems cannot do everything on their own, and integration with other applications is needed.
It would not be a big threat when integration is done between company internal modules, but often, due to cost reduction, developers need to integrate with a system created by other companies.
That leads to emitting a huge amount of data between those companies, so finding the most efficient way can save a lot of time.

## When to use it

In case, if your data structure is complex, the amount of data is ridiculous, you could try to use *Schema Driven Integration*. 
It can be introduced any time, but the earlier you start, the more flawlessly it will work.

Of course, this methodology is not suitable for every project, and most importantly, not for every developer.
To make this hard decision easy, please follow the below diagram:

![Activity diagram for making decision](images/1-activity-diagram.png)

## How to introduce

First of all, you need to know that this methodology is used by the biggest and most famous companies. Do not feel any pressure about it.
Implementing this approach can be done in a few steps.
1. Have a specification defining what you need to achieve with your project. Set up the role of your team, and the role of other company. It would be nice if another company would offer a box-of-the-shelf solution, to reduce costs. Adaptation of the existing system is always cheap.
2. Gather a piece of knowledge about the system that you are creating. Throw a meeting with a company that is making another part of the system.
3. Try to figure out a solution and make a PoC. Make attempts to exchange data through some technology-agnostic protocol.
4. Probably, at this moment you will figure out, that exchanging data in a well-known way is not enough. This is a time when you need to compare your schemas.
5. Prepare a common table schema for the database. Work with another team to produce the best matching schema. See later section for hints.
6. It is almost done! The last step is to set up a way to exchange data. Pick one, all have some pros and cons.

#### Exchange data with Emails

This model of data exchange requires routine for both development team. 
You need to set up constant hours to do backups on one of the databases, pack database dump and secure it with a password.
Once packed, the dump can be sent with email to the second team when someone will unpack and restore it on the other side.
Remember, to distribute the password to dump archive in a secure channel. Some morse code variation is recommended.

Pros:
 * easy to set up, just some agreement needed
 * secures business with constant database dumps, with at least two, georedundant copies. Such stuff usually cost a pile of money
 * whole application is eventually consistent, which is a very fancy topic that you can hear about on every conference
 
Cons:
 * manual work needed
 * backup of the person making a backup is needed in case of day offs, sickness etc.
 * person who is distributing password must be mentally stable and well paid, so it will not reveal a password to other companies in exchange for a bribe
 * will work only if one company is data producer, second is a consumer

#### Database synchronization

Nice and mostly automatic way to distribute data between companies. Databases must be connected into a cluster, and one should operate as primary, and other as secondary.
Usually, databases are supporting such integration as native function, although it might be paid feature.

Pros:
 * automatic process
 * databases are supporting it, even for free
 
Cons:
 * less fancy than exchanging with emails, as eventual consistency is smaller (shorter), so it is not so developer-magnet
 * requires the same database vendor from both system parts, reducing the independence of a team

#### Sharing database instance

This is a higher level of methodology. It requires maturity from developers, managers and companies, on both sides.
Both companies are using the same instance of the database, removing the process of synchronization.

Pros:
 * cost reduction for one of the companies - only one DB instance to maintain
 * both companies are behaving like one living cell, united and bound by something more than just agreement
 
Cons:
 * strong consistency is something that everyone can do and is not fancy at all
 * no data replication, no backups
 * it will take ages in case of database failure to figure out who should fix it
 
## Common table schema for a database

One of the hardest steps is to produce a common data scheme. There are some approaches to modelling it that you might use.

1. Stickers. Write all fields that both systems need, and try to arrange it into tables. You will be amused, how many unneeded columns you will find!
2. Multiply all columns and arrange them into one, wide table. This process is called [Database Normalization](https://en.wikipedia.org/wiki/Database_normalization) and you just satisfied its first form.
3. Ask the other company for their database structure and use the same one in your application.

## Benefits

Apart from self-explanatory benefits, like a chance for eventual consistency, geographical redundancy or regular backups, other things will satisfy not only developers but also management:
 * operating costs are reduced, due to well-defined processes
 * tight cooperation with another company may result in discounts for their later services
 * team members are gathering business-critical knowledge, making feel them important. They will not want to quit their jobs!

---
title: "How I Debug SQL"
date: "2022-11-27"
menu: "main"
description: "Some thoughts"
---


Debugging any type of code is frustrating and tedious. And since the most frequent and most dangerous SQL errors occur even when the code compiles, it can be hard to know where to start when attempting to debug. Moreover, it's not always possible to have a strong instinct on whether or not the returned data is correct, making it all the more crucial to have a process for debugging and double checking your query.

Writing SQL is a huge part of my job, and I've slowly developed a checklist for my debugging to help me step through my code in the most efficient way. Here are those steps that I try to run through:

&nbsp;

####  You Know What They Say About Assuming
- My number one piece of advice is also the most nebulous. Check all the assumptions you might have. It's just as probable that your understanding of a particular table is off than the SQL you're writing is wrong. No assumption in this step is too trivial, take equal caution of each of them

####  Start with Where
- A huge porportion of problems arise from `WHERE` clauses. Manipulating different parts of this section is a good way to make sure that the results change in the way your expect them to.
- If you have multiple conditions -- especially if both `AND` and `OR` are present -- it can be very easy to lose sight of what the behavior is for each. Try changing `ANDs` and `ORs` back and forth as well as commenting out portions. You might be surprised to find the way in which that affects the results

####  One Row per What?
- An important question to ask yourself when you start joining in tables that have different granularities. Should the returned table be one row per user or can a user appear multiple times? When you start aggregating the data it is easy to lose sight of this detail.

####  Standardize you SQL
- If you are part of a larger team where it's necessary for you to read someone else's queries, having conventions for how you write will save you a huge chunk of time. Subqueries vs. CTEs? Will you use `GROUP BY` and `ORDER BY` shortcuts? Even the way you choose to space and format your query is something that your team should be on the same page about. Having these things figured out ahead of time is well worth the investment.

####  Null Comparisons
- Using comparison operators(>=, >, etc.) can have some unexpected results if your data is incomplete. For example, when using these operators on date fields it will filter out all records where the data field is null. Forgeting about something like that can greatly skew your results
####  Know Your Tables
- When inner joining tables make sure the relevant data is consistent in both tables. 
- Some tables might have idiosyncracies that aren't obvious on the surface. For example, your Sales table might have a column for when payment failed. If you go to sum all Sales in that table, it could be important to remember to filter out all cases where payment failed

#### Triple Check
- Did you just find the hidden statistical relationship that is going to 10x your companies revenue? Probably not. Triple check and quadruple check each line in your code. Until you can properly explain each line it might be best to keep that Slack message to the CEO in the drafts.

#### Check the Graveyard
- When spot checking your data make sure to find out what the data isn't showing. Just because the row count matches your number of registered users, doesn't automatically mean you're good to go. Are there any other parts of the query that might accidently contribute to filtering out additional data

#### Use Count Distinct
- Unless you are specifically trying to count rows, you should be using a `DISTINCT` within your `COUNT`. It's very easy to make a mistake that leads to overcounting

--- 
P.S. I'm giving myself credit for not titling this post *CheQList Manfiesto*. That's the type of integrity you can expect from these posts. You're welcome
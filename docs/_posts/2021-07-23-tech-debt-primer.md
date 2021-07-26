---
# DRAFT MODE!!
#layout: post
#title: "Tech debt primer for non-technical people"
#description: "A short introduction to technical debt for people that are not technical"
#date: 2021-07-23 12:03:00 +0100
---

Technical debt. Anyone who has worked near or with software developers have heard of this term, yet very few can actually grasp the meaning of it. I will *attempt* to put this in layman's terms as much as possible, along with throwing in some advices.

For starters, the term is an analogy with actual financial debt. So, let's try to understand that first.

In any debt there are few things involved. 
1. The loaner, kind of obvious, he/she provides the resource that is needed by the other party and expects to get it back.
2. The debtor, the person that lacks the resource and borrows it from the loaner.
3. The resource, what is being borrowed
4. A goal, what the debtor wants to achieve by borrowing the resource.
5. Agreement to pay it back, the how, when and what other considerations are needed to restore the balance.

In the financial example, it's easy to map these elements:
1. The loaner is normally a bank.
2. The debtor is normally you.
3. The resource is money.
4. The goal is to buy something you otherwise couldn't without the loan.
5. The loan agreement, that includes deadlines, interest rates, guarantees and such.

Once you sign the loan agreement, the debt clock starts. If you made the proper budgeting and provisions, you will pay on the given milestones the specified amounts and by the end of the agreement the outstanding balance will be 0 and everyone is happy and debt free.

Now, whenever something extraordinary happens, and for whatever reason you miss a payment, you are breaching the agreement which normally is punished by a delay fee. Here is where things become interesting...

Everytime you miss a payment, few things happen. First, the capital doesn't get reduced.
Second, when the capital doesn't get reduce, the interest amount for the next down payment gets bigger.
Finally, the amount that needs to be paid from now onwards to achieve a 0-balance, is higher: that missed payment and the compounded interest needs to be spread out across the remaining payments ON TOP of the payment itself.

The higher the interest rate the more complicated the problem it becomes when missing a payment.
The more missed payments the harder it becomes to pay the rest of the debt.



## The technicality

We have our primer on debt with a financial example. How does it relate to technical debt?

Let's identify the components
1. Debtor: the developer.
2. Resource: the code and time
3. Goal: build the next feature
4. Loaner: the developer and business pressure.

I will explain in more detail.

The debtor (aka developer), has a goal to achieve (aka build the next feature), for that it needs resources (aka the code and time). The loaner, paradoxically, is the developer as well as it provides the code to work on, and the business pressure provides the time.

The problem occurs when one of those to resources is not (good) enough, something has to give. Bear with me.

If the code is not good enough, is equivalent to having borrow a screwdriver to saw a plank of wood, it can be done... but it will be very hard to do. Moreover, the end result is not going to be nearly as good.

If the time is not enough, you will be force to cut corners. Those cut corners will make the code harder to work with the next round, and with each round of cutting corners the effect is not linear is compound (more on this down below).


## Non-linear growth

Humans are horrible to understand the consequences of compound interest and non-linear growth. We just suck at it.

The following example will illustrate how bad we are at grasping non-linear growth.

There is a pond, where a type of plant grows. This kind of plant doubles in size each day.
By day 43, the pond is fully covered with the plant. Try to guess what day (1-43) the pond was covered half way.

> Just to give you a hint, the actual size of the pond is irrelevant, the actual initial conditions are irrelevant as well.

The answer is counterintuitive. The pond was half full by day 42. The plant doubles in size each day. Day 42 is half full, day 43 is full.

Trivial once explained. I bet you a dollar to a penny that you didn't see that coming.

The same happens with compound interests, we see examples of this during the 2008 market crisis (added to other factors of course).

## Types of technical debt

There are different types of technical debt. I like to call them syntactic tech debt and semantic tech debt. 

Syntactic tech debt is easy to automate, and machines are great at spotting them. We have tools for that: linters, static analysis tools, etc. Most of this tech debt points out to _possible problem causing patterns_. Keyword here: possible. The vast majority of tools have arbitrary rules of what is considered "good" and "bad" patterns. More often than not, there are simply conventions. Almost always, you can build your next feature regardless how many "violations" your code base has. 

The Semantic tech debt, it's more complicated to spot. It is nuanced, and complex for machines to understand. However, **this** is the kind that break things bad. This is the kind that makes developers say to the business: _it can't be done_ or _we need a big refactor for that to happen_.


## How did this happen?

The answer to this question is very simple: It happened slowly but steady. Like a wave carving a stone, just one little each time. You missed payments often and the interest are mounting up.

Everything starts with adding this _if_ here, because it's such a corner case. Or because this is a _temporary_ patch, if it works we will make it right.

Without realizing all this small shortcuts start to pile up, and they become part of the system. When someone new comes, and see a bit of working functionality that is very similar to what they need to do, they copy-paste-adjust for the new needs. Congratulations! the virus has spread and mutated at the same time.

Now try to add a more complex feature... instead of taking the time to think it through (do not confuse with up-front design), we have pressure to hack it in place because there is no time, or there is an advertising campaign that's going live.


## How to repay the debt?

I hear you thinking, _alright, how do I get rid of the debt I have now?_. To what i will answer you: as fast as you can.

Start today, keep it small, and keep it constant. With every story you do, improve something. Anything, but improve something.

Do it relentlessly in every single story (if you work on scrum/kanban) on every task you are going to tackle. Refactor something that is not great, something that looks odd. Dedicate 30min-1h each day to it. No business people will complain about that, would you care?.

There are things that are more broad, you can either: split the work to make it fit in this daily 1 hour improvement or ask for special time to tackle it. The latter will require some convincing to the business people. Business people: this is critical for you too!. If you and your developers let the codebase get to the point where your developers start to tell you _that can't be done_... you both have lost.

You can only be as agile as your codebase allows you to be. A debt-ridden codebase is not agile, it will take long time to deliver features, costing you money, time and frustration on both sides.


## How to avoid the debt?

As with any debt, the best way to avoid is being up-to-date with the payments. Once you have repaid the debt try to keep it that way. 

When a new feature needs to be implemented, take the time, to refactor the code such that the new feature seems to be the part of the system from the beginning. Apply this for every feature you add.

Quality is your best ally in the fight for tech debt, TDD and proper testing helps to improve the design and keep it healthy and allows you to be informed of any regressions.


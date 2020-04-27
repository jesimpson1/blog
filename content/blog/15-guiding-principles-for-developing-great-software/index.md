---
title: 15 Guiding Principles for Developing Great Software
date: "2020-04-27T12:32:10.643Z"
description: These 15 guiding princicples will help you develop great software. Crafted over 20+ years of software development experience, they are the principles I use every day.
---

My first programming job was back in 1996. Fresh out of college here in the UK, I was hired as a junior COBOL programmer. And here we are now, in 2020, and I’m still writing code for a living. And I love it.

During my 24 years (at the time of writing) of commercial software development experience — whether it’s warehouse control software for huge distribution centres or web apps for small, independent businesses — I’ve learned a thing or 2 along the way about writing great code and crafting great software.

My definition of ‘great’ is software that is bug-free, covered by tests, performant, easy to maintain and understand, with reusability wherever it makes sense. And the following principles help me to achieve this. I hope you find them useful.

## Code is for humans
You don’t write code for anything other than people. Even if you’re the sole developer working on the codebase, you should stick by this rule.

There are so many ways to write code, so many different styles, but ultimately its aim is to give you the exact same end result regardless of how it’s written. So write your code so that others (or you, 6 months from now) can read and understand it.

The only caveat to this rule is if what you’re writing is so performance critical you have to write it in a way that’s highly performant but not so obvious as to what it’s doing and why. But if you’re honest with yourself, how often is that?

There’s usually a point in your career where you’re constantly trying to write ‘clever’ code: something that’s a few characters shorter, or just a line or 2 that does something highly complex.

That’s your ego at work. I know because I’ve been there and I see it often in less experienced developers who are starting to get to grips with the requirements of being a great developer… though some never grow out of it.

Keep your ego in check. Make your code so simple any level of developer can read and understand it and, crucially, any level of developer can _maintain it_.

## If you need comments, it might be too complex
If I can, I write really, really simple functions that do one thing so they can be _composed_ to work together. I try to have only one input, one output and no side effects; so ideally, they should be _pure functions_. And those that aren’t pure because of side effects (API call, updating the DOM etc.) I try to contain appropriately.

If I do that, then comments are rarely needed in my code because it’s pretty clear what’s going on. And if there is complexity or question marks, then usually my test cases will cover it and explain why.

I’m not saying you shouldn’t add comments. If they’re needed, they’re needed. But as soon as I start adding a comment it always make me stop and think: am I adding this comment because my code is too complex?

## Your units should have tests, and ideally they should be written first…
AKA Unit Tests. If you write really simple functions, you can write really simply unit tests. One input, one output, no side effects. And this means there are no reasons not to write your unit tests first and follow the practice of Test Driven Development.

However, I’m less strict with other developers about writing tests first when it comes to the teams I work with. In my experience the majority of developers struggle following TDD. They understand the concept and the advantages it brings, yet still tend to write their code first.

I usually find it’s because they’re not breaking down the process enough and trying to get the correct end result in just a handful of large functions. Because of that, they don’t yet know what to properly test for in their units.

The thing is, if you start with your tests and you focus on small, single-responsibility mostly-pure functions, then writing the tests first becomes infinitely easier. And then you’ll find a lot of the code you write can be reused… especially when you start writing higher order functions that can be used and composed in different ways.

But getting into TDD requires a change of mindset, a change of approach, and unlearning old habits. That takes time, patience and practice. Hence me not being too strict on this principle with others… though I always try to nudge them in this direction.

## … and how your units work together should have tests, too
Otherwise known as integration tests.

Your functions are covered by unit tests so you know that given the same input you’ll always get the same output, expect maybe in those cases where you have side effects.

You’ll then usually need those functions to work together in some way to produce an overall end result. That end result is what your integration tests should be testing for.

These tests are the main tests you should be writing. They give you confidence that your units are working together as you intended.

When you’ve got your code covered by unit and integration tests you’re in a position where you can refactor your code with supreme confidence. Make a change, save the file, watch your tests run automatically and, if they pass, your code is sound.

This whole process is otherwise known as _red, green, refactor_: write your tests, which will fail (red). Write your code so the tests pass (green). Change your code so it’s inline with your principles and meets your coding standards (refactor).

Again, it does require a change of mindset. But once you get it through consistent, purposeful practice, you won’t look back.

## Your projects should have universally agreed quality checks
These should form part of your expected criteria to deem the code production-worthy. So things like:

* using a linter to check your code
* using a prettifier to format your code
* having an agreed minimum coverage percentage for tests
* having all tests pass before raising a pull request
* having some form of security validation

… and so on.

Sometimes I’m asked why you’d have a prettifier as part of your ‘quality’ checks. Quite simply, it means everyone is working off of the same blueprint and it helps stop the ‘I’ll fix it later’ mentality that can creep in. It also means when it comes to your peers reviewing your code, there is less cognitive load on them.

Which leads us to…

## Keep cognitive load low
The more you write code for humans, the better the quality checks, the better the tests, the simpler the code overall… the less cognitive load is required by your peers to read and understand your code and what it’s doing, and the less cognitive load on your future self when you come back to the code you’re writing today. Your future self and everyone who touches the code going forward will thank you for it.

You might not be in a position to implement _all_ of these principles, for any number of reasons. If that’s you, spend some time figuring out what you _can_ implement, if only to reduce the cognitive load.

## Don’t get caught up trying to make it perfect
I’ve worked with some great developers throughout my career. I mean, truly great. But some of them take _forever_ to deliver. Why? They want things to be perfect.

They’ll spend hours deliberating over a variable or function name even when the current ones are clear and obvious, or worrying about things they probably won’t need or scenarios that will never happen, or optimisations that make no real-world difference.

The end result being their delivery rate is lower than it could be, potentially putting pressure of their colleagues further down the production line; all of sudden they need a ‘quick’ code review to get it to the test engineers ASAP, who have to work quickly and, potentially, cut corners. This effect compounds the further down the production line the work goes.

Late delivery is a fact of life in software development, but don’t make it late because you’re trying to make your code perfect. ‘Great’ is good enough.

## Micro optimisations are rarely worth it
This is another productivity killer. Spending hours or even days refactoring your code, trying different things to rinse out every possible performance gain you can… all to make a saving that doesn’t mean anything in the real world.

If the software you’re working on requires this level of performance optimisation then fine. But that’s pretty rare, and should be factored into the estimate so the time spent is expected and accounted for.

Just like trying to make your code perfect, micro optimisations are rarely worth it. They kill time for no noticeable gain and put time pressure on those further down the production line.

## Accept there will be bugs
Accept it. Live with it. Don’t beat yourself up when someone finds them in code you’ve written. It’s the nature of the game.

## Leave it better than you found it, or at the very least, no worse
Whenever you have to change existing code, always try to leave it better than you found it. Improve the tests, improve the variable or function names, get rid of that loop-within-a-loop.

Of course, It’s not always possible to do this for any number of reasons, so ensure _at a minimum_ you’re not leaving it any worse than you found it.

## The cost of Technical Debt will eventually cripple any business
Tech debt has to be paid back as soon as possible. Just like financial debt, the longer it’s left the worse the problem gets and the more it costs to get rid of. 

Eventually it will cripple you; you’ll be constantly ‘coding around’ the problem, therefore adding to the debt,  until you finally hit a point where you’re stuck and need a complete rewrite. And a lot of business can’t afford to do that.

If you can, pay back tech debt at the point of finding it. If it means you overrun slightly in terms of your estimates then explain this to whomever you need to (product owner, project manager, whatever) and why it’s so critical. If you can’t pay it back immediately, get it recorded, prioritised and played as soon as possible.

## Humans are terrible at estimating
One of my former bosses used to say of estimates: double it and add 10%.

To be fair, it’s not a bad strategy because most people are pretty terrible at estimating the time needed to complete a story or the complexity of the work required.

The less you know about something, the less accurate your estimate will be. The more complex a task, the less accurate your estimate will be. The larger the task, the less accurate your estimate will be. And if you’re being asked to estimate something you’ve never done before… you guessed it - the less accurate your estimate will be. In fact, if it’s something you’ve never done before your estimate is likely to be wildly inaccurate.

When a product owner or project manager tries to predict a final delivery date based on estimates provided to them by the development teams, I always wince; inaccurate estimates multiplied across multiple stories and multiple epics = wildly inaccurate and effectively pointless estimate.

Make sure you understand this. And make sure the person you report to understands this too.

## When you open a Pull Request, you’re saying “my code is production ready”
If you’re asking for your code to be peer reviewed so it can be merged into the main branch of development (which depends on your workflow) you’re effectively saying your code is ready to go into production.

This means it should pass all of the quality checks, so there is enough test coverage, all tests pass, the code has been linted and prettified, the acceptance criteria has been met etc.

You’re basically saying it’s ready to move forward on the production line to whatever that next step is (which varies depending on the organisation). So, do your due diligence before opening a pull request.

## Don’t slate others’ code
It’s so easy to moan and complain about someone else’s code. It’s so easy to slate their work and tell your colleagues how terrible it is, and at the same time make yourself look awesome by telling them how it should have been done.

The thing is, you don’t know the full story. You don’t know the pressure they were under to deliver. You don’t know the requirements intimately, or the acceptance criteria, or the state-of-mind of the developer at the time. Maybe they were going through a tough time in their lives and the code they were writing wasn’t their main priority. Maybe they were still learning and it was the best they could do at the time. Maybe the senior developers didn’t do their jobs properly by allowing it through code review.

If it’s not up to scratch, improve it; don’t bitch about it in stand up or at the coffee machine.

## Sometimes, it all goes out the window
There are times when you have no choice but to do something quick and dirty. To throw all your guiding principles out the window and to just simply deliver.

Those occasions happen to all developers. For whatever the reason, you just have to grit your teeth and get on with it. Fighting back against it will only cause you frustration and anger; it’s just not worth it. Make your point but don’t hold onto it.

When this inevitably does happen, just accept it, let it go and move on. Create a clean-up task that can be played in the very near future; it means you can put things right and it logs the overhead such decisions make.

## Conclusion
I try to write great software. Of course, occasionally it doesn’t always turn out that way. Sometimes I miss something, or I’m working on legacy code that I can’t rewrite just yet, or whatever. That’s just the way it goes and it’s something that, while I don’t like, I made peace with a very long time ago.

Despite this, I always aim for my definition of ‘great’. Following these principles allows me to do that, and they are the principles I try to impress upon the other developers I work with.
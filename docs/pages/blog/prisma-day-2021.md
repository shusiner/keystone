---
title: "Prisma Day 2021 Talk"
description: "Jed Watson shared Keystone 6 with the world at Prisma Day conference in July 2021. His talk is a great way learn how Keystones combination of features and flexibility set it apart from other backend frameworks and Content Management Systems."
publishDate: "2021-7-16"
authorName: "Ronald Aveling"
authorHandle: "https://twitter.com/ronaldaveling"
metaImageUrl: ""
---

Jed Watson shared Keystone 6 with the world at Prisma Day conference in July 2021. His talk is a great way learn how Keystones combination of features and flexibility set it apart from other backend frameworks and Content Management Systems.

{% youtube url="https://www.youtube-nocookie.com/embed/fPWRlmedCbo?rel=0" label="Next-gen CMS and GraphQL API with KeystoneJS and Prisma - Jed Watson | Prisma Day 2021" /%}

## Video Transcript

Hi everyone, my name is Jed.

I'm from an Australian consultancy called [Thinkmill](https://thinkmill.com.au) and I'm here today to talk to you about the concept of a "Next-Gen CMS".

It's hard to start that without going back to what is a CMS originally. And I think CMS is one of those things on the internet that was kinda the original problem that we solved – there's a lot of content and we needed to manage it.

And back in the day, that meant that you have to handle a huge amount of things. Everything from database to access APIs, pages and modules, it was really quite comprehensive. While that was really good because if you picked up a CMS, you didn't have to build a lot of those things yourself; over time, we realized that it's actually very restrictive having one system doing all these things and CMS, well, it kinda became a dirty word for a while. And eventually, when front-end development in particular moved on, it got so restrictive that front-end developers called a revolution. They said:


> You know what? We don't want this. Just give us the content over an API. We're gonna program the front-end ourselves.

And we did.

And that's where the concept of a **Headless CMS** came from. This is sort of the **second major generation of CMS**. You see a lot of these around today and really what they're doing is just taking care of the backend concerns for content management.

And it's great because as front-end developers we’re now completely liberated to program and deploy our own front-ends. But not everyone's a front-end developer and not all the system logic lives on the front end. So the challenge with this is if you look at Headless CMS as "not just a CMS" but actually in most sites and apps, it's your backend. And if you've got a back-end system that is doing all these things for you in its own opinionated way or closed in a little walled garden, that also becomes a really limiting thing.

What I've learned over the years of building sites and apps and APIs, and even frameworks on the internet, it's that: **the separation that we wish existed between content and data – it's not a real thing. Content always ends up being data. In fact, it's better if it's data**. Most data relates to content. And this puts us in a challenging spot because suddenly, if we want a rich back-end system and we're stuck in a limiting framework, what are we gonna do?

Well, the answer is – we're developers and we're just gonna do it ourselves. The good news is in 2021, it's nowhere near as hard as it used to be. We have much better building blocks to build on when we're putting these things together for ourselves.

Prisma is a great example of one of them. Prisma gives you schema, migrations, queries for the data layer. Like it actually makes programming for databases as a front or even back-end developer, a lot more fun. And that's really cool. I love that it exists.

The thing is if I'm thinking about a website or an app on the internet, it's not all I need. The things I need to put on top of my data layer are things like a GraphQL API, and an Admin UI. These come back to the things that a Headless CMS is solving for us. It's not often that you need to do all the work of putting GraphQL together or all the work of the management UI, but if you don't have them, you can write a lot of code.

And that's why we wrote KeystoneJS.

KeystoneJS is a project that sits on top of Prisma in version six, and **it's here to answer all of the things that a Headless CMS can give us, but do it in a way where we can actually program and deploy it ourselves**.

So on this programming thing, an important point here is that **configuring is not programming**.

Configurable systems, most CMSs out there, no matter whether they're very flexible or quite rigid are configurable but **configurable systems get unwieldy because scope is infinite**. It kinda guarantees two things. One is that you get a lot of stuff that you need for free, or well license, let's just say you get it.

On the other hand, it's not gonna suit you perfectly. And **the more things the program of a configurable system try to add in, the harder it is for them to get the right answer for everyone**.

So **as programmers** on the other hand, **we can write exactly what we want**.

We can **keep things simple by making them specific. And that's what we built Keystone to do: provide high-level building blocks with the low level of flexibility that we really want as developers**. And I think almost uniquely Keystone is really laser-focused on making the developer experience of this really great.

Let me show it to you. If we start with a simple project, we'll write TODO app, I'm gonna add some Keystone dependencies and then I need to set up two files: the first is my Keystone entry point, and the second is a couple of models in my schema. We call them lists.

So here you can see my TODO and my user in their fields. I've marked the email as unique and required. And that's enough to get an app running. If we go to the terminal, we were on keystone-next dev and it's gonna do a few things and to step you through those, the first is gonna do is it's gonna generate some files. One of them is our Prisma schema. You commit this to Git, it's part of your system. You can use it, but Keystone will ensure that it is in sync with your Keystone models. Thee second is a GraphQL schema and all the resolvers and logic that you need behind that. These two files are enough to actually get you two things in your browser.

The first being Keystone's Admin UI which lets us create new things. Use them, edit them, manage them, enlists, mass change or delete them, even filter them based on very similar, very powerful features, just like Prisma client has.

We also get a GraphQL API with all, it's almost like the same API as Prisma client but in GraphQL. So we can query for through relationships across our models. We can run filters, we can count things. We can mutate them, update them, create them, delete them, all those sorts of things.

But then you can **start programming it. And this is where it gets interesting**. If I come back to my entry file and I add in a bit more code now, I'm plugging in an Auth system into Keystone and this Auth system is gonna mean the next time I go to the Admin UI, I get to sign in. It also means that Keystone is gonna manage our sessions, give us mutations for signing in and signing out and forgetting a password, and getting a one-time signing link, all of the sort of stuff that you don't wanna actually build yourself.

I can also take that Auth and come to my schema. And now I can start plugging in access control. And this is again, where **defining a schema in TypeScript is a really important feature** of Keystone.

I can add functions to check the session and see if people should be able to read email addresses or change the admin flag at all. I can set who can access a list to update it.

Either all admins or people can just update the things that belong to them. I can set that across multiple lists and I can also hook into various events like resolving input to make sure that if you're not an admin, you can only create TODO lists that are assigned to you, and you can't create them for someone else.

**This is just touching the tip of the iceberg of a really powerful system, that's not that complex. There's not a ton of configure here because the key is you're just writing JavaScript functions and you're able to program it yourself to do specifically what you want. And we found that to be incredibly powerful.**

So what I've just shown you is a whole lot of create, read, update, delete that you get out of the box but that's not what most systems end up being made of.

It's great on day one. It gets you up and running really quickly but the next trick is to gradually replace it. And Keystone's designed for this as well. We understand at a system level that you're gonna end up over years building a sophisticated application or platform or back-end for a content site. And we wanna support you on that journey.

So here's an example of adding in a schema extension to add statistics to the API, the query or the underlying database which can use the Prisma client to do so. And importantly, they can also relate back to the types and parts of Keystone is providing for you. So you kind of replace and augment what is unique to your app without losing the automation that you got the benefit from, which you haven't needed to eject from. It's not an all or nothing thing.

**Programming Keystone is a really important feature. You can get custom fields, query your database, put your own React views in the Admin UI, write queries and mutations for your logic. You can even tie in third-party microservices and stitch them into your schema.**

**What other CMS can you do that with?**

So there's a lot of other high-level features that you may or may not get benefit from. There are some rich fields like images, different ways of presenting the underlying data primitives that Prisma gives us access to. Also a really, really rich document editor, this is extensible powerful you write basically prop types in your own react component and you get a WYSIWYG experience that manages structured data behind the scenes. This is actually one of the most exciting aspects of the project but I don't have time to deep dive on that today. You can join me in the workshop. I'll be doing a Prisma day as well if you wanna learn more about that but I'll leave you with two thoughts.

One is that I think that we really believe very strongly that **focusing on developer experience is one of the biggest levers you've got for improving user experience** at the end of the day. Keystone has been designed to focus on the code that matters not also get you to write all the code that you didn't need to. It sort of tries to take that off you without blocking you from writing the code that you should be writing. So focus on what's important to your project.

And secondly, it's **designed for developers**. It's designed to fit into your workflow. So DevOps is much, much better than Click-ops. You can commit your schema to get, follow your CI process, run your tests, do branch preview deployments with your back-end as well as your front-end. It really wants to live in your world and not change the way you would have done the project. Just make it easier for you.

And I think that is really for me, **what a Next-Gen CMS is all about. It's all the power of Prisma and GraphQL and a react Admin UI that you can program yourself. That's not blocking you into someone else's system**.

So this is our take on what that looks like. I'd love you to check it out, let us know what you think and enjoy the rest of the conference.

Thanks for having me.

---

If you like using Keystone, we'd appreciate a shout out in [Twitter](https://twitter.com/KeystoneJS) and a star in [GitHub](https://github.com/keystonejs/keystone).
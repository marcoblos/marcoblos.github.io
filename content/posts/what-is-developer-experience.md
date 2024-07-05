---
author: ["Marco Blos"]
title: "What is developer experience?"
date: "2024-06-30"
description: "What is developer experience and some steps to improve it."
tags: ["DeveloperExperience"]
ShowToc: true
---

**TL;DR** development experience is to provide a better and more structured way for developers to understand the systems they work on.

---

What do you see when searching for Development Experience, or DX?

What I usually see is a bunch of articles twisting the term from its essence and trying to address/extract secondary implications, for instance: how to make developers more productive, or let’s create a tool to improve the development experience, but do they really want to improve development experience or just want to find a number to justify their own assumptions?

Despite developers productivity being a real topic it is not the central point of DX. The cern of development experience is to provide a better and more structured way for developers to understand the system they are working on, and as a result, be independent, creative, and perhaps more productive.

Let’s create a hypothetical scenario: a developer joins a new project and is assigned a new task, the task is to modify a function that is triggered by a queue. The developer has no idea how the application works. It does not have instructions about running the application. After a couple of hours trying to trigger this function, to test and understand it, to then be able to modify it, the developer still does not understand why sometimes the function is executed and sometimes it is not.

Now, why is this a development experience problem? Shouldn’t the developer know the system they work on to then be able to modify the system? The short answer is yes, they should know, but let’s be honest, in most companies and projects, developers do not know much about the application itself, they usually know very well some specific parts of the it. Most of us become a junior developer again when joining a new project, all we have are the general and transferable skills accumulated over time.

The longer answer is that it depends on various aspects:

- How experienced (not talking about years in the craft) the developer is?
- How much general knowledge does this developer have?
- Where the application is running?
- How is the application running?
- How much control over the environment this developer has?

After working on several projects, I can confidently say that the root of the problem described above is not the person’s experience, but how they experience software development on the specific project.

To resolve this problem, and give a more pleasant kick-start to new developers joining a project, I would start by looking into the basic aspects of the project:

- Are there instructions on how to run the application?
- Do developers understand how to start and stop the application?
- Are there ways to simulate the development environment as close as the production environment?
- Do developers understand the boundaries of the application?
- How complex are the instructions to be followed?
- Where and how is this information being kept?

It sounds unrealistic, but the problem described above, about the developer not knowing why the function is triggered, is explained by a developer not having an isolated development environment, because the queue is shared between developers. As a result, the queue will deliver the message to whoever gets it first, causing the idea of a flaky environment. This problem usually triggers multiple fixes attempts, extra logs being added, etc., but none of these will provide developers confidence on resolving the problem.

I’ve seen this happening, for over a week, in a big tech company, where multiple developers reported day after day that they could not understand why the messages were processed intermittently. At first, their conclusion was that it should be a problem with the queue, or the library used to poll messages from the queue.

After a week, the problem was a team-wide problem with at least half of the team involved, trying to understand why messages are sometimes processed and sometimes are not. The team settled on a strategy: create a new environment, including new cloud resources. The problem was not observed in the new environment. Messages were always processed, and the problem remained only in the “development environment”.

But how can we avoid this problem? This is the diverging point I have with most people.

The problem described above is not solvable by creating a new tool, by measuring how effective a team is, by measuring how many deployments happen in a period of time, etc. The above problem is solvable by two simple and neglected steps:

1. Create a solid and isolated development environment.
    - Does your software need to use a queue? Create and use this queue in your development environment.
    - Does your software make requests to an external API? Create a mock API and use the mock API for development.
2. Write an exceptional README file
    - Use imperative and simple language
    - Explain how to create the queue and why it is needed. Add commands to create and maintain the queue in the developers machine.
    - Explain how to start and maintain the mock API and why it is needed.
    - Explain that your software has prerequisites to run. Give directions how to make it run properly.

The steps above are the basics of development experience, they contribute to onboarding new developers to the project and reduce friction on “how to do” things.

It is the opposite of some companies' culture of “self-service”. Or is it the real “self-service”?

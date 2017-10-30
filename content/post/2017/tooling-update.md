---
title: "Tooling Update"
date: 2017-10-24T20:56:23+05:30
author: Sahil Ahuja
tags: [ "devops", "react", "mobx", "reactvr" ]
categories: [ "blog" ]
---

While going over different technologies that could be used to augment the existing stack in [GMETRI](http://gmetri.com) (more about that *to be written*) I came across a number of exciting advancements that occurred in the JS world over the last one and a half year. Focusing on creating a startup and with me becoming a father (for the first time) left me with little time to keep up with the latest tech happenings. This post is an attempt to overcome that.

### Motivation

{{< load-photoswipe >}} <!-- needed only once, include after -more- else loads multiple times in list pages ;) -->
{{< figure link="/images/2017/swiss-knife.jpeg" title="Tooling Motivation">}}

While trying to interpret the nagging feeling that something was missing in the way we developed, I went down to my roots. Why do I think I can code well? This reminded me what some of my most complex and well written pieces of code were — Games. Games traditionally are the most difficult (and exciting) pieces of code to write because both the background complexity and the UI are an order of magnitude more complex than the usual day to day apps we are used to.

### Goal
On a personal front am planning to create a simple game to give me a taste of the below tools and frameworks that seem to be missing pieces using this article as a guide. Hopefully yields a good result! ReactNative looks like a good platform to be building it. Also with ReactVR gaining popularity it makes the argument to learn ReactNative and basing all (near term) future development on ReactJS even stronger.

### Treasure Hunt
On the tooling front a search on React yielded a [gold mine](https://codeburst.io/angular-vs-react-which-is-better-for-web-development-e0dd1fefab5b). This article is an opinionated piece on every new building block that I was searching for. Also a very interesting piece of information was that Angular 4 is something that can be seriously looked at for future projects. The only fear is the cost of context switching.

#### Pieces Missing in our current flow — Solution
* Type Checking — [Flow](https://flow.org/en/docs/types/)
* State Manager — [MobX](https://mobx.js.org/)
* Material Design for React — [React Toolbox](http://react-toolbox.com/)
* Form validations — [FormState](https://formstate.github.io/)
* API Layer: [GraphQL](http://graphql.org/learn/)
* Frontend API Caching Layer: [apollo-client](https://github.com/apollographql/apollo-client)
* Type Checking: Flow/TypeScript 2 ([Good comparison](https://djcordhose.github.io/flow-vs-typescript/2016_hhjs.html#/))

The above is list that **_will_** undergo serious changes once the test game is complete. More on that in another post.

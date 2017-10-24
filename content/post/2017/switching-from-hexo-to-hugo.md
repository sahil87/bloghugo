---
title: "Switching From Hexo to Hugo"
author: Sahil Ahuja
date: 2017-10-18T23:56:14+05:30
tags: [ "test", "hugo" ]
categories: [ "blog" ]
---

My first *hugo* blog post.

<!--more-->

Crazy time trying to figure out differences sections, types and layouts. 

Finally the dust settles, with a few compromises.

### TODOs

- [ ] Need to add tags apart from just categories in the template. A nice challenge!
- [X] Need to figure out shortcodes for youtube and fontawesome. (About us page dependent on that)
- [X] To figure out how to publish to sahil.cc (to a separate github repo to allow https)
- [X] Using image in Hugo
- [X] Deciding folder and URL structure of posts
- [X] Finalize default archetype
- [X] Galleries in Hugo (https://github.com/liwenyip/hugo-easy-gallery)
- [X] Copy all posts
- [X] Fix all posts
- [X] Copy all drafts
- [X] Fix disqus comments in theme (TODO: postback a pull request to fix in main theme)
- [X] Fix all drafts
- [ ] Move remaining blogs from [here]({{<ref "post/2016/Hello-World.md" >}})
- [ ] Post in all old blogs that the new blog is now [sahil.cc](http://www.sahil.cc). List [here]({{<relref "post/2016/Hello-World.md#first-things-first" >}})

### Learnings

#### Categorization:
Categorization of posts in happen through two concepts:

1. **Sections:** 
   The 1st level folder under which a post is created in the folder "content" is the section of that post.
   - Type = Section by default. The type can overridden through Front Matter. Sections can't be overridden.
1. **Taxonomies:** 
   Taxonomies are user defined groupings of content. Taxonomies have to be defined in the config file except for `tags` and `categories` which exist by default.

#### Section Structure:
There are ways to disconnect the folder structure from the URL structure in Hugo. Per post this can be accomplished through [front matter](https://gohugo.io/content-management/front-matter/) named url and on a website level the following config achieves the same:
```
[permalinks]
  post = "/:year/:month/:title/"
```

However fatigue prevailed and I decided to go for a structure where there is balance between the number of brain cycles that get extinguished trying to decide where every new post needs to placed and the logical structure of posts on the website. This middle ground was the decision to use only the year in the URL. 

This allows one to achieve the minimum level of segregation required at the filesystem layer, prevents the URL from looking really bad and also informs the user if the post being read is too old (going for month in this case is an overkill). This also allows for zero manipulation of the path to url conversion. 

#### Creating new posts:
See [archetypes](https://gohugo.io/content-management/archetypes/).

Command:
```
hugo new <content-section>/<file-name.md>
```

    Eg: `hugo new post/2017/switching-from-hexo-to-hugo.md`
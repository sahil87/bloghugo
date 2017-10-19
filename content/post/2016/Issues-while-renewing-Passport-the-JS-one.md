---
title: Issues while renewing Passport - the JS one
date: 2016-11-25 05:24:39
tags:
  - web
  - authentication
  - rants
  - express
categories: [review]
author: Sahil Ahuja
---

No, am not talking about my actual passport, which also needs to be renewed soon by the way. Am talking about PassportJS.
<!--more-->

Continuing my rant over the not so good login infrastructure avaible - the following were the gotchas we faced while implementing passportjs:

1. Passport requires a callbackURL when initialzing it. Thanks to https://github.com/jaredhanson/passport-facebook/issues/2 we found out it could also be specified while calling the strategy.
1. Passport assumes the developer will do most of the route wiring. A very important prerequisite is the flow of control in it's documentation. Hint - it's not there. Found a great blog post detailing the same: http://toon.io/understanding-passportjs-authentication-flow/
1. A much hidden pattern in Passport is the verification of the access_token itself. After much hue and cry, found it to be the following:
   * **Google**: `https://www.googleapis.com/oauth2/v1/tokeninfo?access_token=${user.access_token}`
   * **Facebook**: `https://graph.facebook.com/debug_token?access_token=${fb_app_id}|${fb_app_secret}&input_token=${user.access_token}`
   When a request is made to the above URLs, a response code of 200 signifies that the token is valid. 

And now for the cool features of Passport that weren't that obvious at first:
1. **Normalized profiles**: When authenticating using a third-party service such as Facebook or Twitter, user profile information is often available. Each service tends to have a different way of encoding this information. To make integration easier, Passport [normalizes profile information](http://passportjs.org/docs/profile).
1. Probably not the place for this, but express supports [callback chaining](http://expressjs.com/en/api.html#router.METHOD). So potentially before the final route callback we can put many as many authentication/authorization callbacks as we want.  Eg: 
   ```javascript
   router.get(
     '/authenticated/route/', 
     (req, res, next)=>{doAuthentication(); next();},
     (req, res, next)=>{doAuthorization(); next();},
     (req, res, next)=>{res.render(page);},
   );
   ```
   which is what passport.authenticate is - one of these callbacks

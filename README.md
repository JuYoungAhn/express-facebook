This example is based on this link.
https://github.com/passport/express-4.x-facebook-example
The only difference is view engine. not ejs but jade.
It will be your start application using facebook authentication application with jade view engine.

## Instructions

To install this example on your computer, clone the repository and install
dependencies.

```bash
$ git clone https://github.com/JuYoungAhn/express-facebook
$ cd express-facebook
$ npm install
```

### server.js
Fill in your client id and client secret.
```js
passport.use(new FacebookStrategy({
    clientID: FACEBOOK_APP_ID,
    clientSecret: FACEBOOK_APP_SECRET,
    callbackURL: "http://localhost:3000/auth/facebook/callback"
  },
  function(accessToken, refreshToken, profile, cb) {
    User.findOrCreate({ facebookId: profile.id }, function (err, user) {
      return cb(err, user);
    });
  }
));
```
## Start App
```bash
$ node server.js
```

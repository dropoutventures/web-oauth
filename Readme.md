web-oauth
===========
A simple oauth API for ~~node.js~~ the web, something we can use on serverless platforms.  This API allows users to authenticate against OAUTH providers, and thus act as OAuth consumers.

Tested against Twitter (http://twitter.com), term.ie (http://term.ie/oauth/example/), TwitPic, and Yahoo!

Also provides rudimentary OAuth2 support, tested against facebook, github, foursquare, google and Janrain.   For more complete usage examples please take a look at connect-auth (http://github.com/ciaranj/connect-auth)

[![Clone in Koding](http://learn.koding.com/btn/clone_d.png)][koding]
[koding]: https://koding.com/Teamwork?import=https://github.com/ciaranj/node-oauth/archive/master.zip&c=git1
[![Pair on Thinkful](https://tf-assets-staging.s3.amazonaws.com/badges/thinkful_repo_badge.svg)][Thinkful]
[Thinkful]: http://start.thinkful.com/node/?utm_source=github&utm_medium=badge&utm_campaign=node-oauth

Installation
============== 
```bash
npm install oauth
```

Examples
==========
## OAuth1.0
```javascript
describe('OAuth1.0',function(){
  var OAuth = require('oauth');

  it('tests trends Twitter API v1.1',function(done){
    var oauth = new OAuth.OAuth(
      'https://api.twitter.com/oauth/request_token',
      'https://api.twitter.com/oauth/access_token',
      'your application consumer key',
      'your application secret',
      '1.0A',
      null,
      'HMAC-SHA1'
    );
    oauth.get(
      'https://api.twitter.com/1.1/trends/place.json?id=23424977',
      'your user token for this app', //test user token
      'your user secret for this app', //test user secret            
      function (e, data, res){
        if (e) console.error(e);        
        console.log(require('util').inspect(data));
        done();      
      });    
  });
});
```

## OAuth2.0 
```javascript
describe('OAuth2',function(){
  var OAuth = require('oauth');

   it('gets bearer token', function(done){
     var OAuth2 = OAuth.OAuth2;    
     var twitterConsumerKey = 'your key';
     var twitterConsumerSecret = 'your secret';
     var oauth2 = new OAuth2(server.config.keys.twitter.consumerKey,
       twitterConsumerSecret, 
       'https://api.twitter.com/', 
       null,
       'oauth2/token', 
       null);
     oauth2.getOAuthAccessToken(
       '',
       {'grant_type':'client_credentials'},
       function (e, access_token, refresh_token, results){
       console.log('bearer: ',access_token);
       done();
     });
   });
```

Contributors (In no particular order)
=====================================

* Evan Prodromou
* Jose Ignacio Andres
* Ted Goddard
* Derek Brooks
* Ciaran Jessup - ciaranj@gmail.com
* Mark Wubben - http://equalmedia.com/
* Ryan LeFevre - http://meltingice.net
* Raoul Millais
* Patrick Negri - http://github.com/pnegri
* Tang Bo Hao - http://github.com/btspoony
* Damien Mathieu - http://42.dmathieu.com
* Luke Baker - http://github.com/lukebaker
* Christian Schwarz  - http://github.com/chrischw/
* Joe Rozer - http://www.deadbytes.net
* Garrick Cheung - http://www.garrickcheung.com/
* rolandboon - http://rolandboon.com
* Brian Park - http://github.com/yaru22
* José F. Romaniello - http://github.com/jfromaniello
* bendiy - https://github.com/bendiy
* Andrew Martins - http://www.andrewmartens.com
* Daniel Mahlow - https://github.com/dmahlow
* Pieter Joost van de Sande - https://github.com/pjvds
* Jeffrey D. Van Alstine
* Michael Garvin
* Andreas Knecht
* AJ ONeal
* Philip Skinner - https://github.com/PhilipSkinner
* Tom Ciborski - https://ciborski.com/

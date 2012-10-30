# prez

!SLIDE

# LyonJS

## lyonjs.org

!SLIDE

## Let's start

``` javascript
var cluster = require('cluster');
var http = require('http');
var numCPUs = require('os').cpus().length;

if (cluster.isMaster) {

  for (var i = 0; i < numCPUs; i++) {
    cluster.fork();
  }

} else {

  http.createServer(function(req, res) {
    res.writeHead(200);
    res.end("hello world\n");
  }).listen(8000);

}
```

!SLIDE

## Learn once, use everywhere

![mobile](http://www.chrome-os.net/wp-content/uploads/2012/08/Firefox-OS1.jpg)

!SLIDE

## Mobile

![jquery mobile](http://jquerymobile.com/wp-content/uploads/2012/09/jquery-mobile-logo_positive.png)

!SLIDE

## Mobile

![phonegap](http://blog.ippon.fr/wp-content/uploads/2012/04/phonedap-logo.png)


!SLIDE

## Learn once, use everywhere
![tablet](http://www.lionnelweb.com/blog/wp-content/uploads/2012/03/ipad-web-design-templatemoonster.jpg)

!SLIDE

## Learn once, use everywhere
![personnal computer](http://www.linternaute.com/hightech/micro/dossier/donner-une-seconde-vie-a-son-pc/image/pc4-hightech-micro-342017.jpg)

!SLIDE

## On personnal computer

![Internet Explorer](http://magazine.qualys.fr/wp-content/uploads/internet-explorer.jpeg)

!SLIDE

## On personnal computer

![Windows 8](http://itechbook.net/wp-content/uploads/2012/08/windows-8-logo-9.png)


!SLIDE

## On personnal computer

![Ubuntu Unity](http://www.journaldugeek.com/files/2012/01/ubuntu-logo.gif)


!SLIDE

## On personnal computer

![Gnome Shell](http://joesteiger.com/wp-content/uploads/2011/07/gnome3logo.jpg)


!SLIDE

## Learn once, use everywhere

![data center](http://www.007hebergement.com/img/data_center.jpg)


!SLIDE

## DataBase

![MongoDB](http://af83.com/media/post_image/69/big_logo-mongodb-onwhite.png)

``` javascript
person = db.people.findOne( { name : "sara" } );
person.city = "New York";
db.people.save( person );
```

!SLIDE

## in the JVM

![Rhino](https://developer.mozilla.org/@api/deki/files/832/=Rhino.jpg)

!SLIDE

## badass APIs boosted by V8

![nodejs](http://upload.wikimedia.org/wikipedia/en/a/a7/Nodejs_logo_light.png)


!SLIDE

# What can we do with nodejs ?


!SLIDE

## Sexy command line interfaces

<iframe width="560" height="315" src="http://www.youtube.com/embed/vFacaBinGZ0" frameborder="0" allowfullscreen></iframe>


!SLIDE

## Manipulate the DOM on the Server

``` javascript
var jsdom = require("jsdom");

jsdom.env(
  '<p><a class="the-link" href="https://github.com/tmpvar/jsdom">jsdom\'s Homepage</a></p>',
  ["http://code.jquery.com/jquery.js"],
  function(errors, window) {
    console.log("contents of a.the-link:", window.$("a.the-link").text());
  }
);
```

!SLIDE

## Optimize you web assets

* [uglifyjs](https://github.com/mishoo/UglifyJS)
* [html-minifier](https://github.com/kangax/html-minifier)
* [css-base64-images](https://github.com/Filirom1/css-base64-images)

!SLIDE

## Script easily

<http://documentup.com/arturadib/shelljs>

``` javascript
require('shelljs/global');

if (!which('git')) {
  echo('Sorry, this script requires git');
  exit(1);
}

// Copy files to release dir
mkdir('-p', 'out/Release');
cp('-R', 'stuff/*', 'out/Release');

// Replace macros in each .js file
cd('lib');
ls('*.js').forEach(function(file) {
  sed('-i', 'BUILD_VERSION', 'v0.1.2', file);
  sed('-i', /.*REMOVE_THIS_LINE.*\n/, '', file);
  sed('-i', /.*REPLACE_LINE_WITH_MACRO.*\n/, cat('macro.js'), file);
});
cd('..');
```

!SLIDE

## Reverse proxy

* <https://github.com/nodejitsu/node-http-proxy>
* <https://github.com/dotcloud/hipache>
* <http://apiaxle.com/>

!SLIDE

## Ease multi-core programming

* One process per core
* Message passing between processes

``` javascript
var cluster = require('cluster');
var http = require('http');
var numCPUs = require('os').cpus().length;

if (cluster.isMaster) {

  for (var i = 0; i < numCPUs; i++) {
    cluster.fork();
  }

} else {

  http.createServer(function(req, res) {
    res.writeHead(200);
    res.end("hello world\n");
  }).listen(8000);

}
```

!SLIDE

## Ease Concurrent Programming

* Non blocking APIs
* Single Loop

!SLIDE

## Cloud Ready

* Heroku
* Cloud Foundry
* Nodejitsu
* Nodester
* ...

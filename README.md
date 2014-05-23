js-project
========

##Work in progress...
Not everything is working as it should yet.

Seed/scaffold/skeleton for a new javascript or node project using html-builder
and bb-server

Features:

* Automatic rebuilding of site when files change
* Refreshes browser when files change
* On the fly transpiling of source files by the server, which are then cached by
  bb-server, so write your code in coffeescript for example, add it to your page
  and stop worrying about it.
* All static resources are cached by bb-server, in memory and on disk. If any
  original file changes only that file gets retranspiled, reminified and/or
  gzipped. 
* Organise code in nodejs modules for use in the browser (without browserify)
* Automatic production mode when environment variable is set
* Stamping of files for caching purposes. So send out static resources with an
  infinite expire time.
* Minify and gzip all resources
* Write your html in snippets, then compose these to make bigger snippets, and
  then a full page.
* Server can serve single page application
* Server can serve phantomjs prerendered pages if a request for an escaped
  fragment comes in
* Server is basically a static file server, write your own request handlers for
  any non-static resource request, separated out by method (GET, POST etc). With
  a bit of hacking you could implement route handling, just call require
  fileHandler and pass on the request if there's no applicable route
* More..


For info on how configure html-builder see
[builder/recipe.js](https://rawgithub.com/Michieljoris/html-builder/master/docs/example-recipe.html).

For info on how configure bb-server see [server/server.js](https://rawgithub.com/Michieljoris/bb-server/master/docs/example-server.html).

Clone or copy repo.

Then:

	mv ./js-project ./your-new-project-name
    cd ./your-new-project-name

Make sure node, npm and bower are installed.

eg: node install -g bower

Edit package.js and bower.js and enter required packages under dependencies.

Run
    
	./init
	
This will insert your project name in the right places, install bower and npm
packages, create a default README.md, create a default javascript file in src
and its docco in docs, and initialize a new git repo. 

Edit build/recipe.js to set asset requests and their paths.

Edit server/server.js to configure the node server.

Set bin/URL to the address:port the app gets served from.

To serve:

	bin/serve	
	
To build:

    bin/build
	
Run them in separate terminals and monitor both. See configuration for both
bb-server and html-builder on how to enable a socket connection between these
two and the browser for auto refresh on any changes to the hmlt/js/css.	
	
If you don't need a server and/or a build tool remove the build, certs, server and
www directories according to your needs.

Edit package.js and bower.js then

    node package.js
	
or
    
	node bower.js
	
to update package.json and bower.json respectively. Version numbers get bumped.

Execute 

    bin/docs
	
to create docco for the javascript file with the projects name in the docs directory.

Make sure to start scripts in ./bin from the site's directory.	

The init script is made non-executable to prevent mishaps, since it removes your
.git directory and starts a new repo.
	

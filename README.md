js-scaffold
========

Seed/scaffold/skeleton for a new javascript or node project using html-builder and bb-server

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

To serve only:

	bin/serve-forever
	
To develop:

    bin/develop
	
If you don't need a server and/or a build tool remove the build, certs, server and
www directories according to your needs.

Edit package.js and bower.js then

    node package.js
	
or
    
	node bower.js
	
to update package.json and bower.json respectively.

Execute 

    bin/docs
	
to create docco for the javascript file with the projects name in the docs directory.

Make sure to start scripts in ./bin from the site's directory.	

The init script is made non-executable to prevent mishaps, since it removes your
.git directory and starts a new repo.
	

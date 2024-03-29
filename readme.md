# node-enliven-minetest

Manage minetestserver using a convenient web interface.

Authentication for players via the mt auth db is planned
(see status at issue #2)!

Before using this webapp, make sure you have installed minetest to
$HOME/minetest with the RUN_IN_PLACE option (this option is true by
default in Final Minetest builds). In the future, this webapp should
ask you which minetest to use: track the progress of this feature at
issue #5.

The webapp must run as same user as minetestserver, and neither should
run as root.


## Install
* Using Terminal, cd to your EnlivenMinetest/webapp directory, then:
```bash
npm install
```


## Features
- Upload skins.
- See Issue #2 for status of planned core feature set before use!


## Usage
* Start the server:
  `node server.js`\
  The server will create the public/skins directory automatically.\
* To force updating skins during startup, delete the public/skins
  directory if already exists and is outdated.
* In browser, go to http://localhost:64638
* For security, no overwriting of existing skins is allowed until
  authentication is implemented: See Issue #2 for status of the planned
  core feature set.


## Developer Notes

This project uses passport
(see <https://code.tutsplus.com/tutorials/authenticating-nodejs-applications-with-passport--cms-21619>

### Development Log
(for changelog, see CHANGELOG.md)
```bash
#!/bin/sh
sudo apt update
sudo apt install nodejs npm mongodb
# NOTE: mongo daemon is called mongod
target_dir=$HOME/enlivenode
if [ ! -d "$target_dir" ]; then
  print "ERROR: Nothing done since missing $target_dir"
  exit 1
fi
cd "$target_dir"
npm init
#except changed jade to pug
npm install express static-favicon morgan cookie-parser body-parser debug pug passport passport-local mongoose multer mv
#NOTE: multiparty has streaming like busboy, but is non-trivial to implement
```

### Not tried yet
(These are things that may help with development or become part of the project)
- [ ] icomoon.io: (generates a font using symbols you choose) has
  symbols for websites and applications (more consistent and bold than
  many in the noun project).
- [ ] LineAwesome: outline version of FontAwesome's symbols
- [ ] ForkAwesome: infinitely scalable vector graphics; 744 icons
- [ ] github.com/RyanZim/EJS-Lint: add it to a quality script
- [ ] How to save form data to MongoDB with Node.js [UPDATED]
  <https://youtube.com/watch?v=rOfT83_eKWk>
- [ ] getbootstrap.com/docs/4.3/components/badge/
- [ ] Link to database(s) directly:
  <https://itnext.io/express-knex-objection-painless-api-with-db-74512c484f0c>
  - handles PostgreSQL/MySQL/SQLite/others
- [ ] [MERN stack A to Z: Part 1](https://blog.logrocket.com/mern-stack-a-to-z-part-1/)
- [ ] Strapi: open-source headless Node.js CMS
- [ ] augmented-ui: "Futuristic, cyberpunk-inspired UI shaping for any
  element; Add the "augmented-ui" attribute to equip the augs"


### Old (Unused)

```
#!/bin/sh
wget https://raw.githubusercontent.com/ericf/express-handlebars/master/examples/basic/server.js
wget https://raw.githubusercontent.com/ericf/express-handlebars/master/examples/basic/package.json
mkdir views
cd views
wget https://raw.githubusercontent.com/ericf/express-handlebars/master/examples/basic/views/home.handlebars
mkdir layouts
cd layouts
wget https://raw.githubusercontent.com/ericf/express-handlebars/master/examples/basic/views/layouts/main.handlebars

if [ -d ../layouts ]; then
  cd ..
fi
if [ -d ../views ]; then
  cd ..
fi
```

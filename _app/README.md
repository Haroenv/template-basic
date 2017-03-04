# <%= projectName %> [![built with choo v4](https://img.shields.io/badge/built%20with%20choo-v4-ffc3e4.svg?style=flat-square)](https://github.com/yoshuawuyts/choo)

Choo-cli created a directory structure that [we've found to be optimal](https://github.com/yoshuawuyts/choo-handbook/blob/master/content/guides-designing-for-reusability.md) for slim
applications and reusability.

```txt
assets/        images and fonts, if you have any
elements/      standalone application-specific elements
lib/           generalized components, should be moved out of project later
models/        choo models
pages/         views that are directly mounted on the router
scripts/       shell scripts, to be interfaced with through `npm scripts`
client.js      main application entry; programmatic manifest file
package.json   manifest file
```

You can use choo-cli to generate pieces of your project as you are developing.
For example you can generate

Pages
```bash
$ choo generate page my-page
```

Models
```bash
$ choo generate model my-model
```

Elements
```bash
$ choo generate element my-element
```

## npm scripts

Choo-cli was made for generating choo projects and code, and leverages npm scripts
for certain project task. So in our project a set of npm scripts have already
been generated that perform various tasks such as testing/serving/building/etc.

At any time you can review the complete list of `npm scripts` available by viewing
[package.json](./package.json) or by running the following command:

```
$ npm run
```

Here is complete list the the commands and their function

- serve:dev - start dev server at [localhost:8080](http://localhost:8080)
- build:prod - builds your project to deploy to a server
- start - a production server (run after `build:prod`)
- test - runs unit tests, for now it will just run linting.
- lint - runs standard against your code

So for example you can run `npm run serve:dev` to start a dev server. You can now see your
app running at [localhost:8080](http://localhost:8080)

## Deploying

Deploying via this method is pretty straight-forward

service|how
---|---
[now.sh](https://now.sh)|`npm run build:prod && now`
[surge.sh](https://surge.sh)|`mv src/index.html src/200.html && npm run build:prod && surge build`
[github pages](https://pages.github.io)|`mv src/index.html src/404.html && npm run build:prod && echo "push the build directory to gh-pages"`
other|`npm run build:prod && npm run start`

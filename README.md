## While "$ npm run watch" is running, if a file in a directory is modified, then run a custom script

I have the following dummy `Laravel 5.5 + React` project:

```
$ git clone https://github.com/tlg-265/laravel-5.5-react.com
$ cd laravel-5.5-react.com
$ npm i
$ npm run watch
```

**My goal is:** while: `$ npm run watch` is running, whenever some of the files: `/template/template-XX.json` is modified, the script `/template/listener.js` be executed.

When that happens, the variable: `template` (inside: `listener.js`) should get the name of that modified file (`JSON` file above), for example: `template-02.json`.

Here is the content of file `/template/listener.js`:

```
var template = '###TBD###';
console.log(`The template: ${template} was modified.`);
```

Probably one way to achieve that is to configure the file: `package.json` accordingly. This is the content of file: `package.json`:

```
{
  "private": true,
  "scripts": {
    "dev": "npm run development",
    "development": "cross-env NODE_ENV=development node_modules/webpack/bin/webpack.js --progress --hide-modules --config=node_modules/laravel-mix/setup/webpack.config.js",
    "watch": "cross-env NODE_ENV=development node_modules/webpack/bin/webpack.js --watch --progress --hide-modules --config=node_modules/laravel-mix/setup/webpack.config.js",
    "watch-poll": "npm run watch -- --watch-poll",
    "hot": "cross-env NODE_ENV=development node_modules/webpack-dev-server/bin/webpack-dev-server.js --inline --hot --config=node_modules/laravel-mix/setup/webpack.config.js",
    "prod": "npm run production",
    "production": "cross-env NODE_ENV=production node_modules/webpack/bin/webpack.js --no-progress --hide-modules --config=node_modules/laravel-mix/setup/webpack.config.js"
  },
  "devDependencies": {
    "axios": "^0.17",
    "babel-preset-react": "^6.23.0",
    "bootstrap-sass": "^3.3.7",
    "cross-env": "^5.1",
    "jquery": "^3.2",
    "laravel-mix": "^1.0",
    "less": "^3.11.1",
    "less-loader": "^5.0.0",
    "lodash": "^4.17.4",
    "react": "^15.4.2",
    "react-dom": "^15.4.2"
  }
}
```

Any idea on how to achieve that?

Thanks!
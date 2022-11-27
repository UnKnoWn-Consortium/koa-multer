# [**koa-multer-esm**](https://github.com/UnKnoWn-Consortium/koa-multer-esm)

[![NPM version][npm-img]][npm-url]
[![NPM Downloads][downloads-image]][npm-url]
[![License][license-img]][license-url]

Route middleware for Koa that handles `multipart/form-data` using [multer][] refactored in authentic ESM. CJS module is also generated via ESBuild. 

This module is a ESM fork of [@koa/multer](https://github.com/koajs/multer) which is a fork of [koa-multer][], the most widely used multer middleware in the koa community.


## Install

> Note that you must install either `multer@1.x` (Buffer) or `multer@2.x` (Streams):

```sh
npm install --save koa-multer-esm multer
```


## Usage

```js
import Koa from "koa";
import Router from "@koa/router";
import multer from "koa-multer-esm";

const app = new Koa();
const router = new Router();
const upload = multer(); // note you can pass `multer` options here

// add a route for uploading multiple files
router.post(
  '/upload-multiple-files',
  upload.fields([
    {
      name: 'avatar',
      maxCount: 1
    },
    {
      name: 'boop',
      maxCount: 2
    }
  ]),
  ctx => {
    console.log('ctx.request.files', ctx.request.files);
    console.log('ctx.files', ctx.files);
    console.log('ctx.request.body', ctx.request.body);
    ctx.body = 'done';
  }
);

// add a route for uploading single files
router.post(
  '/upload-single-file',
  upload.single('avatar'),
  ctx => {
    console.log('ctx.request.file', ctx.request.file);
    console.log('ctx.file', ctx.file);
    console.log('ctx.request.body', ctx.request.body);
    ctx.body = 'done';
  }
);

// add the router to our app
app.use(router.routes());
app.use(router.allowedMethods());

// start the server
app.listen(3000);
```


## Contributors

| Name                   | Website                         |
| ---------------------- | ------------------------------- |
| **Nick Baugh**         | <http://niftylettuce.com/>      |
| **Imed Jaberi**        | <https://www.3imed-jaberi.com/> |
| **UnKnoWn-Consortium** |                                 |


## License

[MIT](LICENSE) © Fangdun Cai


##

[npm-img]: https://img.shields.io/npm/v/@koa/multer.svg?style=flat-square

[npm-url]: https://www.npmjs.com/package/koa-multer-esm

[license-img]: https://img.shields.io/badge/license-MIT-green.svg?style=flat-square

[license-url]: LICENSE

[downloads-image]: https://img.shields.io/npm/dm/@koa/multer.svg?style=flat-square

[multer]: https://github.com/expressjs/multer

[koa-multer]: https://github.com/koa-modules/multer

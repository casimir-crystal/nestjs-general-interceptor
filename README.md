# nestjs-general-interceptor

> **This is a simple copy from [NestJS document](https://docs.nestjs.com/interceptors) and [StackOverflow answer](https://stackoverflow.com/a/60195396/5299236).** 
> > but it works out of the box.

This package is a Nest.js interceptor, it makes your controllers response to this general format:

```json
{
  "statusCode": 200,
  "message": "ok",
  "data": "<Your orgin return data>"
}
```

If your controller thrown an Exception, it does nothing like the documented base example.

## Installation

You can install the package from
[npm registry](https://www.npmjs.com/). Installation is done using command
[`npm install` ](https://docs.npmjs.com/getting-started/installing-npm-packages-locally):

```sh
$ npm install nestjs-general-interceptor
```

## Usage

Within your Nest.js `main.ts`, import and use this module like the example below:

```javascript
import { NestFactory } from '@nestjs/core';
import { AppModule } from './app.module';
import { TransformInterceptor } from 'nestjs-general-interceptor';

async function bootstrap() {
  const app = await NestFactory.create(AppModule);
  
  // This is for global, which wrappers all your controllers
  app.useGlobalInterceptors(new TransforInterceptor());
  
  await app.listen(3000);
}

bootstrap();
```

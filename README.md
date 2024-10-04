# webgl-read-pixels-async

## Context
By default, read pixels is syncronous, which means when you sending readPixels command you can't do anything else until it's done. In performance critical applications, this can be a problem. This library allows to read pixels asynchronously, so you can do other things while waiting for pixels to be read.

Basically, this is an implementations from [MDN's example of reading pixels from webgl2 context asynchronously](https://developer.mozilla.org/en-US/docs/Web/API/WebGL_API/WebGL_best_practices#use_non-blocking_async_data_readback)

## Installation

```bash
npm install webgl-read-pixels-async
```

## Usage

```javascript
const {readPixelsAsync} from 'webgl-read-pixels-async';

const gl = canvas.getContext('webgl2');
const width = canvas.width;
const height = canvas.height;
const pixels = new Uint8Array(width * height * 4);

readPixelsAsync(gl, 0, 0, width, height, gl.RGBA, gl.UNSIGNED_BYTE, pixels)
  .then(() => {
    // do something with pixels
  });
```

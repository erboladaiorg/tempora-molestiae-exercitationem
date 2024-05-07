## Readable Stream Clone

npm install @erboladaiorg/tempora-molestiae-exercitationem

with this utility you can pipe readable stream into multiple writable streams

### Node
```js
const fs = require("fs");
const { ReadableStreamClone } = require("@erboladaiorg/tempora-molestiae-exercitationem");

const readStream = fs.createReadStream('text.txt');

const readStream1 = new ReadableStreamClone(readStream);
const readStream2 = new ReadableStreamClone(readStream);

const writeStream1 = fs.createWriteStream('sample1.txt');
const writeStream2 = fs.createWriteStream('sample2.txt');

readStream1.pipe(writeStream1)
readStream2.pipe(writeStream2)
```

### Typescript
```ts
import * as fs from 'fs';
import { ReadableStreamClone } from '@erboladaiorg/tempora-molestiae-exercitationem';

const readStream = fs.createReadStream('text.txt');

const readClone1 = new ReadableStreamClone(readStream);
const readClone2 = new ReadableStreamClone(readStream);

const writeStream1 = fs.createWriteStream("text1.txt");
const writeStream2 = fs.createWriteStream("text2.txt");

readClone1.pipe(writeStream1);
readClone2.pipe(writeStream2);
```

### Helper functions
Wait till a writable stream finishes writing
```ts
import { promisifyWriteStream } from '@erboladaiorg/tempora-molestiae-exercitationem';

const writeStream = fs.createWriteStream("SomeFile.txt");
await promisifyWriteStream(writeStream);
```

Wait till all the writable streams finish writing
```ts
import { promisifyWriteStreams } from '@erboladaiorg/tempora-molestiae-exercitationem';

const writeStream1 = fs.createWriteStream(fileName1);
const writeStream2 = fs.createWriteStream(fileName2);
await promisifyWriteStreams([writeStream1, writeStream2]);
```
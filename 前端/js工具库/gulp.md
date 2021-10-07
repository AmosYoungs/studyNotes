## requireDir

```
var requireDir = require('require-dir');
requireDir('./out/src/build/build/common');
requireDir('./out/src/build/build/test');
requireDir('./out/src/build/build/business');
```

当一个gulp文件要执行很多任务的时候，为避免文件过大过长，会把task分别写在不同的js文件中，通过使用requireDir引入文件夹，gulp会加载该文件目录下所有js的任务


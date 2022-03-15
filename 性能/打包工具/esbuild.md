# esbuild

> esbuild是最近比较火的编辑工具，在有些领域已经开始替代webpack和babel
> 我们目前 web 构建工具的速度大约是上述工具的 10 - 100 倍。 esbuild 构建工具的核心目标是开创构建工具性能的新时代， 同时创建一个易于使用的现代构建工具。

主要特性：

- 极快的速度，无需缓存
- 支持 ES6 和 CommonJS 模块
- 支持对 ES6 模块进行 tree shaking
- [API](https://esbuild.docschina.org/api/) 可同时用于 JavaScript 和 Go
- 兼容 [TypeScript](https://esbuild.docschina.org/content-types/#typescript) 和 [JSX](https://esbuild.docschina.org/content-types/#jsx) 语法
- 支持 [Source maps](https://esbuild.docschina.org/api/#sourcemap)
- 支持 [Minification](https://esbuild.docschina.org/api/#minify)
- 支持 [plugins](https://esbuild.docschina.org/plugins)

### 一：速度优越性比较

![image-20220311165553126](https://cdn.jsdelivr.net/gh/hjc0826/map-depot@main/uPic/2022-03-11 16:55:53 image-20220311165553126.png)

#### 它是用Go语言编写的，编译成可执行代码

Javascript必须基于解释器的node环境才能执行，所以当webpack等工具解释完自身代码后，可能esbuild已经完成编译工作了，而这时候webpack才能开始执行编译。

此外Go的核心设计是并行的，而Javascript不是。

Go有线程之间的内存共享，而Javascript则必须在线程之间进行数据序列化。

Go和Javascript都有并行的垃圾收集器，但Go的堆实在所有线程之间共享的，而Javascript的每个线程都有一个独立的堆。Javascript工作线程并行量减少了一半，因为还有一半CPU核心正在忙着为另一半收集垃圾。




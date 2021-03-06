项目文件冗余检测工具
检测项目文件夹中的资源有没有被项目使用到，没被用到的会被标记为冗余文件，去除项目冗余文件，让项目更方便持续维护。

仅支持___非webpack___打包项目，`webpack`打包的项目，请使用`tree-shaking`

# Getting Started

```javascript
npm install gulp-unusedfile-check --save-dev
```

# Usage

```javascript
let fu = require('gulp-unusedfile-check');
gulp.task("fu", () => {
    return gulp.src("build_artifacts")
        .pipe(fu({
            ignoreList: ['ry.json', 'main.html'],
            createFile: true,
            debug: true,
            fileDir: "build"
        }))
        .pipe(gulp.dest("find-unused"))
})

```

# Options

## ignoreList

Type:Array Default value:[]

一个忽略检测的文件的列表

## createFile

Type:Boolean Default value:false

是否把检测结果输出到一个独立的文件中


## fileDir

`createFile`为`true`的情况下，这个值才有用

Type:String Default value:跟gulp.src的参数保持一致。

要输出的文件的路径


## debug

Type:Boolean Default value:false

是否打印日志信息

# Release History

|日期|版本|说明|
|---|---|---|
|2017-11-22|v0.3.4| 有原gulp-find-unused迁移到同程前端账号下，同时进行更名为gulp-unusedfile-check，更有利于维护开发 |
|2017-11-23|v0.3.0| 修复生成的JSON文件被当做项目文件进行扫描而导致的冗余文件结果错误的BUG |
|2017-11-23|v0.2.0| 支持打印冗余文件总大小 |
|2017-11-22|v0.1.0| 初次提交 |

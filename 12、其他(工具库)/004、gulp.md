### gulp 打包配置文件 `gulpfile.js`

```javascript
// 在这里书写 guoxiangshop 这个项目的打包配置
// 1-1. 导入 gulp 这个第三方模块
const gulp = require('gulp')

// 1-2. 导入 gulp-cssmin 这个第三方模块
const cssmin = require('gulp-cssmin')

// 1-3. 导入 gulp-autoprefixer 这个第三方模块
const autoprefixer = require('gulp-autoprefixer')

// 1-4. 导入 gulp-uglify 这个第三方模块
const uglify = require('gulp-uglify')

// 1-5. 导入 gulp-babel 这个第三方模块
const babel = require('gulp-babel')

// 1-6. 导入 gulp-htmlmin 这个第三方模块
const htmlmin = require('gulp-htmlmin')

// 1-7. 导入 del 这个第三方模块
const del = require('del')

// 1-8. 导入 gulp-webserver 这个第三方模块
//    导入以后可以得到一个函数
const webserver = require('gulp-webserver')
//1-9. 导入 gulp-sass 这个第三方模块
const sass = require('gulp-sass')
//1-10.导入 gulp-rev 这个第三方模块
const rev = require('gulp-rev')
//1-11.导入 gulp-rev-collector 这个第三方模块
const revCollector = require('gulp-rev-collector')

if (process.argv[2] === 'dev') {
  // 1. 先写一个打包 css 的方法
  const cssHandler = () => {
    return gulp.src('./src/css/*.css')   // 找到 src 目录下 css 目录下 所有后缀为 .
      .pipe(gulp.dest('./dist/css'))  // 压缩完毕的 css 代码放在 dist 目录下的 css 文件夹里面
  }

  //2. 先写一个打包 sass 的方法
  const sassHandler = () => {
    return gulp.src('./src/sass/*.scss')
      .pipe(sass())
      .pipe(gulp.dest('./dist/css'))  // 压缩完毕的 css 代码放在 dist 目录下的 css 文件夹里面
  }

  // 3. 书写一个打包 js 的方法
  const jsHandler = () => {
    return gulp.src('./src/js/*.js') // 找到文件
      .pipe(babel({
        presets: ['@babel/env']
      })) // 转码 es6 转换成 es5 了, 就可以压缩了
      .pipe(gulp.dest('./dist/js')) // 把压缩完毕的放入文件夹
  }

  // 4. 书写一个打包 html 的方法
  const htmlHandler = () => {
    return gulp.src('./src/pages/*.html') // 找到要压缩的 html 文件
      .pipe(gulp.dest('./dist/pages')) // 把压缩完毕的放到一个指定目录
  }

  // 5. 书写一个移动 image 文件的方法
  const imgHandler = () => {
    return gulp.src('./src/images/**') // images 文件夹下的所有文件
      .pipe(gulp.dest('./dist/images')) // 放到指定目录就可以了
  }

  // 6. 书写一个移动 icon 文件的方法
  const iconHandler = () => {
    return gulp.src('./src/icon/**') // icon 文件夹下的所有文件
      .pipe(gulp.dest('./dist/icon')) // 放到指定目录就可以了
  }

  // 7. 书写一个移动 lib 文件的方法
  const libHandler = () => {
    return gulp.src('./src/lib/**')
      .pipe(gulp.dest('./dist/lib'))
  }

  // 8. 书写一个任务, 自动删除 dist 目录
  const delHandler = () => {
    // 这个函数的目的就是为了删除 dist 目录使用的
    return del(['./dist'])
  }

  // 9. 书写一个配置服务器的任务
  const serverHandler = () => {
    return gulp.src('./dist') // 找到我要打开的页面的文件夹, 把这个文件夹当作网站根目录
      .pipe(webserver({ // 需要一些配置项
        host: 'localhost', // 域名, 这个域名可以自定义
        port: 8080, // 端口号, 0 ~ 65535, 尽量不适用 0 ~ 1023
        open: './pages/index.html',
        livereload: true, // 自动刷新浏览器 - 热重启       
      })) // 开启服务器
  }

  // 10. 自动监控文件
  const watchHandler = () => {
    // 监控着 src 下的 css 下的所有 .css 文件, 只要一发生变化, 就会自动执行一遍 cssHandler 任务
    gulp.watch('./src/css/*.css', cssHandler)
    gulp.watch('./src/js/*.js', jsHandler)
    gulp.watch('./src/pages/*.html', htmlHandler)
    gulp.watch('./src/lib/**', libHandler)
    gulp.watch('./src/images/**', imgHandler)
    gulp.watch('./src/icon/**', iconHandler)
    gulp.watch('./src/sass/*.scss', sassHandler)
  }

  // 导出一个默认任务
  module.exports.dev = gulp.series(
    delHandler,
    gulp.parallel(cssHandler, sassHandler, jsHandler, iconHandler, htmlHandler, imgHandler, libHandler),
    serverHandler,
    watchHandler
  )

} else if (process.argv[2] === 'build') {
  // 1. 先写一个打包 css 的方法
  const cssHandler = () => {
    return gulp.src('./src/css/*.css')   // 找到 src 目录下 css 目录下 所有后缀为 .
      .pipe(autoprefixer())   // 把 css 代码自动添加前缀
      .pipe(cssmin())  // 压缩 css 代码
      .pipe(rev())
      .pipe(gulp.dest('./dist/css'))  // 压缩完毕的 css 代码放在 dist 目录下的 css 文件夹里面
      .pipe(rev.manifest())
      .pipe(gulp.dest('./rev/css'))
  }

  //2. 先写一个打包 sass 的方法
  const sassHandler = () => {
    return gulp.src('./src/sass/*.scss')
      .pipe(sass())
      .pipe(autoprefixer())   // 把 css 代码自动添加前缀
      .pipe(cssmin())  // 压缩 css 代码
      .pipe(rev())
      .pipe(gulp.dest('./dist/css'))  // 压缩完毕的 css 代码放在 dist 目录下的 css 文件夹里面
      .pipe(rev.manifest())
      .pipe(gulp.dest('./rev/css'))
  }

  // 3. 书写一个打包 js 的方法
  const jsHandler = () => {
    return gulp.src('./src/js/*.js') // 找到文件
      .pipe(babel({
        presets: ['@babel/env']
      })) // 转码 es6 转换成 es5 了, 就可以压缩了
      .pipe(uglify()) // 压缩
      .pipe(rev())  //给文件名添加哈希值
      .pipe(gulp.dest('./dist/js')) // 把压缩完毕的放入文件夹
      .pipe(rev.manifest())
      .pipe(gulp.dest('./rev/js'))
  }

  // 4. 书写一个打包 html 的方法
  const htmlHandler = () => {
    return gulp.src(['./rev/**/*.json','./src/pages/*.html'])
      .pipe(revCollector({
        replaceReved: true //根据之前生成的json配置，替换原来路径为哈希路径
      }))
      .pipe(htmlmin({ // 想进行压缩, 需要在这个对象里面进行配置
        removeAttributeQuotes: true, // 移出属性上的双引号
        removeComments: true, // 移除注释
        collapseBooleanAttributes: true, // 把值为布尔值的属性简写
        collapseWhitespace: true, // 移除所有空格, 变成一行代码
        minifyCSS: true, // 把页面里面的 style 标签里面的 css 样式也去空格
        minifyJS: true, // 把页面里面的 script 标签里面的 js 代码给去空格
      })) // 压缩
      .pipe(gulp.dest('./dist/pages')) // 把压缩完毕的放到一个指定目录
  }

  // 5. 书写一个移动 image 文件的方法
  const imgHandler = () => {
    return gulp.src('./src/images/**') // images 文件夹下的所有文件
      .pipe(gulp.dest('./dist/images')) // 放到指定目录就可以了
  }

  // 6. 书写一个移动 icon 文件的方法
  const iconHandler = () => {
    return gulp.src('./src/icon/**') // icon 文件夹下的所有文件
      .pipe(gulp.dest('./dist/icon')) // 放到指定目录就可以了
  }

  // 7. 书写一个移动 lib 文件的方法
  const libHandler = () => {
    return gulp.src('./src/lib/**')
      .pipe(gulp.dest('./dist/lib'))
  }

  // 8. 书写一个任务, 自动删除 dist 目录
  const delHandler = () => {
    // 这个函数的目的就是为了删除 dist 目录使用的
    return del(['./dist'])
  }

  // 9. 书写一个配置服务器的任务
  const serverHandler = () => {
    return gulp.src('./dist') // 找到我要打开的页面的文件夹, 把这个文件夹当作网站根目录
      .pipe(webserver({ // 需要一些配置项
        host: 'localhost', // 域名, 这个域名可以自定义
        port: 8080, // 端口号, 0 ~ 65535, 尽量不适用 0 ~ 1023
        open: './pages/index.html',
        livereload: true, // 自动刷新浏览器 - 热重启       
      })) // 开启服务器
  }

  // 10. 自动监控文件
  const watchHandler = () => {
    // 监控着 src 下的 css 下的所有 .css 文件, 只要一发生变化, 就会自动执行一遍 cssHandler 任务
    gulp.watch('./src/css/*.css', cssHandler)
    gulp.watch('./src/js/*.js', jsHandler)
    gulp.watch('./src/pages/*.html', htmlHandler)
    gulp.watch('./src/lib/**', libHandler)
    gulp.watch('./src/images/**', imgHandler)
    gulp.watch('./src/icon/**', iconHandler)
    gulp.watch('./src/sass/*.scss', sassHandler)
  }

  // 导出一个默认任务
  module.exports.build = gulp.series(
    delHandler,
    gulp.parallel(cssHandler, sassHandler, jsHandler, iconHandler,  imgHandler, libHandler),
    htmlHandler,
    serverHandler,
    watchHandler
  )
}
```




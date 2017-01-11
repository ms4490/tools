# tools
常用工具

==========================================================================================================================================
## node.js
https://nodejs.org/en/
==========================================================================================================================================
## grunt
> npm install -g grunt-cli全局安装命令  
> npm install grunt安装命令
### 插件
> npm install grunt-contrib-uglify --save-dev 混淆压缩  
> npm install grunt-contrib-watch --save-dev 监视文件  
> npm install grunt-contrib-jshint --save-dev 检查js语法  
> npm install grunt-contrib-cssmin --save-dev 压缩css  
> npm install grunt-contrib-concat --save-dev 合并  
### package.json
```
{  
  "name": "",//名字  
  "version": "1.0.0",//版本  
  "devDependencies": {  
    "grunt": "^1.0.1",  
    "grunt-contrib-concat": "^1.0.1",  
    "grunt-contrib-cssmin": "^1.0.1",  
    "grunt-contrib-jshint": "^1.0.0",  
    "grunt-contrib-uglify": "^1.0.1",  
    "grunt-contrib-watch": "^1.0.0",  
    "grunt-rev": "^0.1.0",  
    "grunt-usemin": "^3.1.1"  
  }  
}
```
### Gruntfile.js
```
module.exports = function(grunt) {
  // 插件配置
  grunt.initConfig({
    pkg: grunt.file.readJSON('package.json'),
    //uglify配置
    uglify: {
      options: {
        banner: '/*! <%= pkg.name %> <%= grunt.template.today("yyyy-mm-dd") %> */\n'
      },
      build: {
        src: '',
        dest: ''
      }
    },
    //concat配置
    concat: {
      options: {
        separator: ';',
      },
      dist: {
        src: [],
        dest: '',
      }
    },
    //wacth配置
    watch: {
        build: {
            files: [],
            tasks: ['jshint', 'uglify', 'concat', 'cssmin']
        }
    },
    //cssmin配置
    
  });
  // 加载任务插件
  grunt.file.defaultEncoding = 'UTF-8';
  grunt.loadNpmTasks('grunt-contrib-uglify');
  grunt.loadNpmTasks('grunt-contrib-jshint');
  grunt.loadNpmTasks('grunt-contrib-concat');
  grunt.loadNpmTasks('grunt-contrib-watch');
  grunt.loadNpmTasks('grunt-contrib-cssmin');
  // 默认被执行的任务列表
  grunt.registerTask('default', ['jshint', 'uglify', 'concat', 'cssmin','watch']);
};
```

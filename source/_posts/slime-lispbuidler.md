title: slime-lispbuidler
date: 2015-10-06 19:09:13
categories: lisp
tags: lispbuidler
---
common lisp调用sdl图形库
<!--more-->
首先，安装好sdl,sdl-gfx,sdl-mixer,sdl-ttf,sdl-image这些库，图形库.
在debian下，如安装sdl,sdl-gfx
```bash
#sudo aptitude install libsdl1.2-dev ;;大概会是这样，比如要是其他版本，会有提示
#sudo aptitude isntall libsdl-gfx1.2-dev  ;;
```
然后，用ee发来得那个quicklisp里面，
```lisp
cl-user>(load "~/quicklisp/setup.lisp")
cl-user>(quicklisp-quickstart:install)
cl-user>(ql:add-to-init-file)

cl-user>(ASDF:OPERATE 'ASDF:LOAD-OP :lispbuilder-sdl)
cl-user>(asdf:operate 'asdf:load-op :lispbuilder-sdl-gfx)
cl-user>(asdf:operate 'asdf:load-op :lispbuilder-sdl-mixer)
cl-user>(asdf:operate 'asdf:load-op :lispbuilder-sdl-image)
cl-user>(asdf:operate 'asdf:load-op :lispbuilder-sdl-ttf)
cl-user>(asdf:operate 'asdf:load-op :lispbuilder-sdl-examples)
```
一个实例
```lisp
cl-user>(sdl-examples:fireworks)
```
或者，可以把lispbuilder下载，clone 这个 https://github.com/lispbuilder/lispbuilder.git ，下载后，一个一个添加进去，具体看lispbuilder的文档吧...
```lisp
cl-user>(pushnew "~/path/to/lispbuilder/lispbuilder-sdl" asdf:*central-registry* :test #'equal)
cl-user>(asdf:operate 'asdf:load-op :lispbuilder-sdl)
```
或者，(这个暂时没有尝试过,意思嘛，大家都明白的)
```lisp
(require :asdf)
(dolist (dir (directory "~/path/to/lispbuidler/*/"))
        (pushnew dir asdf:*center-registry* :test #'equal))
```


## flowconfig 配置文件
### [include]
  告知flow 还需要检测哪些文件或者目录(所有子目录)。 这一栏配置的每一行表示一个检测路径， 可以使用相对于根目录的路径或者绝对路径，支持一个或多个星号通配符。

### [ignore]
  告知flow哪些文件不需要检测，路径匹配使用正则表达式。 通常应该以 .* 开头

    [ignore]
    .*/src/\(\)/.*

### [libs]
  告知flow检测代码时， flow会包含指定的声明(接口文件); libs下的每行配置要包含一个目录或文件， 相对与根目录的路径或者绝对路径。

### [options]
  支持多个键值对。 任何未设置的配置项都有默认值。 有一些配置项可以通过命令行标记(--xx)覆盖。

    1. log.file(string): 日志文件路径(默认 /tmp/flow/<根目标转义>.log)
    
    2. module.name_mapper('正则'->'字符串'): 正则用来匹配模块名， 字符串表示替换后的模块。
    如：
    module.name_mapper='^image![a-z0-9A-Z$_]+$' -> 'ImageStub
    让 flow 认为require('image!foo.jpg)就是 require('ImageStub')
    
    3. module.system(node|haste): 使用哪种模块系统解析 import | require, 默认是node;

    4. module.system.node.resolve_dirname(string): 默认flow 会在 node_modules目录下查找 node模块， 通过这个配置更改查找目录: 


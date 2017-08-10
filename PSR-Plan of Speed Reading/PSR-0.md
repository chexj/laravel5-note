# Mandatory
# 强制的
+ A fully-qualified namespace and class must have the following structure \<Vendor Name>\(<Namespace>\)*<Class Name>
+ 一个完整的命名空间和类应该拥有以下结构： \<Vendor Name>\(Namespace\)*<Class Name>
+ Each namespace must have a top-level namespace (“Vendor Name”).
+ 每一个命名空间必须有一个顶级的命名空间，即 Vendor Name.
+ Each namespace can have as many sub-namespaces as it wishes.
+ 每一个命名空间可以拥有任意多的子命名空间。
+ Each namespace separator is converted to a DIRECTORY_SEPARATOR when loading from the file system.
+ 每一个 命名空间分隔符 从文件系统加载时都会被转成 目录分隔符。
+ Each _ character in the CLASS NAME is converted to a DIRECTORY_SEPARATOR. The _ character has no special meaning in the namespace.
+ 类名中的 '_' 符号会转成目录分割符， '_' 符号在命名空间中没有任何特殊意义。
+ The fully-qualified namespace and class are suffixed with .php when loading from the file system.
+ 一个完整的命名空间和类 从文件系统加载时会被加上 '.php' 后缀。
+ Alphabetic characters in vendor names, namespaces, and class names may be of any combination of lower case and upper case.
+ 插件名，命名空间和类名中的字母可以是 大小写字母的任意组合。

# Example Implementation
# 实例

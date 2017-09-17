# SQL学习笔记

--------------------------------
1. 检索数据（select)
+ 基本语句（`select xx from xx`)

+ 限制结果 (`select xx from xx limit n` --表示取回不多余n行
          `select xx from xx limit n, m` 或 `select xx from xx limit m offset n` --表示从n开始取，取回不多余m行)

+ 排序数据 (`select xx from xx order by xx` --表示按xx排序，默认升序
          `select xx from xx order by xx1, xx2`, .. --表示按多列排序，只有在前面的列数据相同的情况下，才按下个列排序，默认升序
          `select xx from xx order by xx DESC` --表示按xx排序，降序
          `select xx from xx order by xx1 DESC, xx2 DESC`, .. --表示按多列排序，如果要降序，必须每列都使用`DESC`关键字
          `select xx from xx order by xx1 DESC limit 1`, .. --降序和限制结合，表示取一列中的最大值，limit要处于order by之后)

+ 过滤数据 (`select xx from xx where xx=xx` 数据应该在数据库过滤，不应该在应用层过滤
          `select xx from xx where xx=xx order by xx` --如果有排序子句，`order by`应该在`where`后面
          `where`子句操作符
          `=` 等于
          `<>` 不等于
          `!=` 不等于
          `<` 小于
          `>` 大于
          `<=` 小于等于
          `>=` 大于等于
          `BETWEEN` 在指定的两值之间
          `select xx from xx where xx between x and y` --表示范围检查，x和y要用and连接
          `select xx from xx where xx is null` 或者 `select xx from xx where xx is not null`--表示空值或非空值检查
          `select xx from xx where xx=x and yy=y` --AND操作符
          `select xx from xx where xx=x or yy=y` --OR操作符
          `select xx from xx where (xx=x or zz=z) and yy=y` --AND操作符优先级大于OR操作符，所以需要使用括号表示正确的意思
          `select xx from xx where xx in (yy, zz)` --IN操作符,与OR操作符完成相同的功能，但是语法更优雅，功能更强大
          `select xx from xx where xx= not in (yy, zz)` --NOT操作符,用于取反
          通配符匹配
          `LIKE` 关键字
          `%` 表示任何字符出现任意次数,但是不能匹配null `select xx from xx where xx like "%x%"` --通配符搜索模式
          `_` 表示单个字符，只能匹配一个任意字符 `select xx from xx where xx like "_x"`
          注意：
          mysql匹配时默认不区分大小写
          where条件中字符串要加‘’引号，数值不用

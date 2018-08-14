# Mongoengine



### 连接

`connect`

```bash
connect（db = None，alias ='default'，** kwargs ）
```

### 多数据库支持

`register_connection`

```bash
register_connection(
	alias="default",
    db=None,
    name=None,
    host=None,
    port=None,
    username=None,
    password=None
    )
```

`models`中切换

```python
from MongoEngine import *

class User(Document):
    name = StringField()
    meta = {
        "db_alias": "default"
    }
```

### 字段

`StringField`	字符串

`URLField`		Url

`EmailField`		邮箱地址字段

`Intfield`		32位整数

`LongField`		64位整数

`FloatField`		浮点数字段

`DecimalField`	定点十进制

`BooleanField`	布尔

`DateTimeField`	时间

`ComplexDateTimeField`	精确毫秒级时间

`EmbeddedDocumentField`	嵌入式文档，有声明的document_type

`GenericEmbeddedDocumentField`	通用嵌入式文档

`DynamicField`	动态字段类型

`ListField`		列表字段

`EmbeddedDocumentListField`	嵌入式有文件的List字段

`SortedListField`	排序的列表字段，确保始终检索为已排序的列表

`DictField`			字典

`MapField`			名称映射到指定字段

`ReferenceField`		文档引用

```bash
# 使用reverse_delete_rule可以处理删除字段引用的文档时应该发生的情况。
DO_NOTHING（0） - 不做任何事情（默认）。
NULLIFY（1） - 更新对null的引用。
CASCADE（2） - 删除与参考相关的文档。
拒绝（3） - 防止删除参考对象。
PULL（4） - 从ListField参考文献中拉出参考

初始化参考字段。

参数：	
dbref - 将引用存储DBRef 为ObjectId.id 或.id。
reverse_delete_rule - 确定删除引用对象时要执行的操作
```



`LazyReferenceField`

`GenericReferenceField`

`BinaryField`		二进制数据字段

`FileField`			GirdFS存储字段

`ImageField`			图像文件存储字段

`SequenceField`

`ObjectIdField`

`UUIDField`

`GridFSProxy`

`ImageGridFsProxy`

`ImproperlyConfigured`



### 查询

> all()

​	返回所有文档

> all_fields()

​	包括所有字段

```python
post = BlogPost.objects.exclude('comments').all_fields()
```

> as_pymongo()

​	返回的不是Document实例 而是pymongo值

> batch_size()

`	限制单个批处理中返回的文档书

> clone()

​	创建副本

> comment(text)

​	查询中添加注释

> count(with_limit_and_skip=False)

​	数量

> create(**kwargs)

​	创建新对象，返回保存的对象实例

> delete（*write_concern = None*，*_from_doc_delete = False*，*cascade_refs = None* ）

​	删除查询匹配 的文档
                                       |

> exec_js(*code*, *fields, **options)

​	执行js代码
                                                         |

> fields（*_only_called = False*，**\* kwargs* ）

​	处理如何加载此文档的字段

仅包含字段的子集：

```python
posts = BlogPost.objects().fields（author = 1，title = 1）
```

排除特定字段：

```python
posts = BlogPost.objects().fields（comments = 0）
```

要检索数组元素的子范围：

```python
posts = BlogPost.objects().fields（slice__comments = 5）
```

> filter()

​	过滤, 别名`__call__()`

> first()

​	匹配的第一个对象

> from_json(json_data)

​	将json数据转换为未保存的对象

> hint(index=None)

​	提示， 在对多个字段进行查询时，将索引字段作为提示传递，若索引不存在，提示不会执行任何操作

​	可以极大提高查询性能

> in_bulk(object_ids)

​	通过其id检索一组文档

> insert()

​	批量插入文档

> item_frequencies（*field*，*normalize = False*，*map_reduce = True* ）

​	返回整个查询文档集中字段中存在的所有项的字典及其对应的频率。这对于生成标记云或搜索文档很有用。

> limit(n)

​	返回的文档数限制为n，也可以用切片,如`User.objects[:5]`

> max_time_ms(ms)

​	服务器上终止查询前等待ms毫秒

> modify(*upsert = False*，*full_response = False*，*remove = False*，*new = False*，**\* update* )

​	更新并返回更新的文档。

​	基于新 参数返回修改之前或之后的文档。如果没有文档与查询匹配且upsert为false，则返回`None`。如果		upserting和new为false，则返回`None`。

​	如果full_response参数是`True`，则返回值将是来自服务器的整个响应对象，包括'ok'和'lastErrorObject'字段，而不仅仅是修改后的文档。这很有用，主要是因为'lastErrorObject'文档包含有关命令执行的信息。
                                                             |

> next()

​	将结果包装在document对象中

> no_cache()

​	转换非缓存查询集

> no_dereference()

​	解除对此查询集的结果引用

> no_sub_classes()

​	仅返回此文档实例，不返回继承文档

> only()

​	仅加载此文档的子集

only（）是可链接的并且将执行union ::所以使用以下内容它将同时获取：title和author.name：

```
post = BlogPost.objects.only('title').only('author.name')
```

> order_by(*keys)

​	结果通过key来指定顺序，升降序

> scalar(*field)

​	不返回document实例，按顺序返回特定值或元组值

​	可以与`no_dereference()`关闭解除一起使用

> search_text(text,language=None)

​	使用文本索引开始文本搜索

> skip(n)

​	返回结果前跳过n个文档

> timeout(enabled)

​	查询时启用或禁用默认的超时

> to_json()

​	将查询集转换为json

> update(*upsert = False*，*multi = True*，*write_concern = None*，*full_result = False*，**\* update* )

​	更新
                                                   |


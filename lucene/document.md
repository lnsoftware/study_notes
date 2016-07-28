# Document, Field 核心

Field 类中有几个重要的属性配置：IndexOptions，。。。

## IndexOptions（替换老版本的TermVector，Index）
枚举值，主要在索引时存储的信息量多少。并不是信息存储得越多越好，因为一是浪费静态存储空间和动态运行时内存，比如日期类型的字段，我们不会去做向量空间对比，权重排序，只是做简单查询和过滤，所以出现的次数或者所在的位置就不是那么重要。
 
## Field
### boost
每个 Document 都是由多个 Field 组成， 我们在检索查询时，提供的字段关键词的影响权值不是相同的，比如一个网页，可以标题就比内容占有更高的权值，通过设置 Field 的 boost 值来影响各字段的权值。

### Norm
normilization，针对每个 Field 词项长度做规一化处理。即越长的内容，其 norm 值越低。当某个字段其长度比较一致平衡时，可以设置 omitNorm，节约存储和计算量。
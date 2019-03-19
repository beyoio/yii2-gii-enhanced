# yii2-gii-enhanced
yii2 Gii增强版扩展。

## 1.为何编写此扩展?
yii2 gii可以很方便生成CRUD界面，特别是针对后台开发，能极大提升开发效率。
但是作者在实际中发现有几个几个问题：
1. 列表页和详情页使用GridView/DetailView，得非常熟悉GridView/DetailView的用法，才能定制它。另外这种方式对web前端工程师非常不友好，导致页面调整非常困难。最终的问题就是本来是属于web前端的工作，却不得不由php开发人员承担，导致错位任务产生。
2. 搜索行为必须再新建立SearchModel并从Ar model继承，这将导致产生不必要的SearchModel
文件，我们期望复用Ar model，以达到代码结构简洁直观。
3. 没有字段与表单控件的绑定机制。yii2的gii生成的表单，只有单行文本框和多行文本框，导致生成的表单相当鸡肋。 但实际中，往往会存在select/radio/checkbox/datetime/date等形式的表单控件, 例如状态,应该是一个select, 性别应该表现为radiolist, 标签应该表示为checkbox。birthday表现为文本框，同时应该附加一个日期插件。
4. 缺少字段输出的格式化，比如timestamp应该格式化为日期时间。status应该显示对应值的文本标签。

## 2. 此扩展提供了哪些特性？
1. 列表和详情页舍弃GridView/DetailView，直接生成直观的HTML代码，无论是PHP开发者还是web前端，可以直观上手定制之。
2. 字段与表单控件类型自动适配，只要按规则定义好字段的类型，就能自动生成相应类型的表单控件。
3. 搜索表单舍弃SearchModel,不必生成额外的model文件，保持代码结构清晰。
4. 实现单控制器，多action的路由模式, 即所有crud共用一个控制器，每个action代表了一个model的crud操作，这样view文件自然就位于同一个目录中，维护浏览也方便直观一些。
官方的gii为每张表生成控制器，导致controller过多，view文件分散。
5. 兼容bootstrap3/bootstrap4两种样式，取决于配置。



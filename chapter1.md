# 1.[库文件介绍](http://wiki.bsdn.org/pages/viewpage.action?pageId=75071567) {#title-heading}

# 概述 {#id-3.库文件介绍-概述}

我们知道，在进行具体规则配置之前，需要先定义规则需要用到的BOM对象，一般来说，我们项目当中的BOM有三种类型：一种是与具体业务数据对应的实体对象，比如Hibernate或iBatis中的实体对象等；一种是一些可枚举的值，比如人员实体对象的学历、性别、职位等，这些值一般是有限且固定的，所以是可枚举的；第三种就是一些在计算过程当中产生的临时值，这些值可能不会被持久化，但计算过程中需要有这些值作为参考。

```
   在URule当中分别提供了三种类型的库文件来对应可能需要的三种类型的BOM，分别是用变量库文件来定义与具体业务数据对应的实体对象，用常量来定义枚举值，用参数来定义计算过程当中产生的临时值。除此之外，URule中还提供了一个用于映射后台Java类方法的动作库文件，该文件可映射一个在spring中配置好的bean的方法，这样就可以在具体在规则中通过动作库文件调用这些后台Java方法。
```

# 变量库文件 {#id-3.库文件介绍-变量库文件}

```
   运行一个包含urule-console模块的项目，打开URule Console控制台，创建一个新的项目，在项目的资源节点下有个名为“库”的点，在这个节点上右键就可以创建变量库文件，实际上所有库文件都是在这个节点下创建的，如下图所示：
```

![](http://wiki.bsdn.org/download/attachments/75071567/var-create.png?version=2&modificationDate=1527734213000&api=v2&effects=border-simple,shadow-kn)

操作提示

如果你创建的项目中资源节点下没有“库”节点，那是因为你修改了项目知识库内容的展示方式，点击左上角![](http://wiki.bsdn.org/download/attachments/75071567/list-type.png?version=1&modificationDate=1475123343000&api=v2)，在弹出的菜单中选择“分类展示”，这样就可以看到“库”节点。

在URule当中，通过这个功能可以修改项目知识库内容的展示方式，选择“分类展示”，就可以看到上图所示效果，将项目中的库文件、决策集文件、决策表文件、评分卡文件、决策流文件分类存放展示；如果选择“集中展示”，那么就不会对这些文件进行分类，统一放在资源节点下。

需要注意的是，在“分类展示”模式下，如果创建有目录，那么这个目录会出现在所有的分类下，同样如果在某个分类下删除某个目录，那么这个目录也将会从所有的分类中删除，创建目录也是一样。在“集中展示”模式下，因为不进行分类，所以目录就不存在这种现象，这点需要注意。

在添加文件或目录时，目录或文件名只能使用英文，不支持使用中文，及其它非法字符。

```
   创建好变量库文件后，可以看到系统会用变量库编辑器自动打开这个文件，在这个编辑器中，首先需要添加变量的分类，然后再添加具体的变量字段。对应到Java实体对象，就是要添加对应的实体对象信息，再添加这个实体对象所拥有的属性信息。如下图所示：
```

![](http://wiki.bsdn.org/download/attachments/75071567/var.png?version=3&modificationDate=1527734346000&api=v2&effects=border-simple,shadow-kn)

```
   添加一个分类，输入名称，这个名称是对当前分类的描述，会在规则中直接引用显示，所以一般我们会使用中文描述来作为名称，类路径，就是这个分类对应的实体类的完整路径，比如com.bstek.entity.Customer，如下图所示：
```

![](http://wiki.bsdn.org/download/attachments/75071567/var.png?version=3&modificationDate=1527734346000&api=v2&effects=border-simple,shadow-kn)

```
   这时，变量的分类就定义好了，如果当前定义的类路径对应的类在当前应用中存在的话，那么我们可以点击“操作列“中的第一个![](http://wiki.bsdn.org/download/attachments/75071567/flush.png?version=1&modificationDate=1475124489000&api=v2)按钮，这样系统就会通过Java的反射功能生成当前类对应的所有字段信息。上图中com.bstek.entity.Customer类源码如下所示：
```

**Customer类源码**

| 12345678910111213141516171819202122232425262728 | `packagecom.bstek.entity;importjava.util.Date;importcom.bstek.urule.model.Label;/*** @author Jacky.gao* @since 2016年9月29日*/publicclassCustomer {@Label("名称")privateString name;@Label("年龄")privateintage;@Label("出生日期")privateDate birthday;@Label("等级")privateintlevel;@Label("手机号")privateString mobile;@Label("性别")privatebooleangender;@Label("是否有车")privatebooleancar;@Label("婚否")privatebooleanmarried;@Label("是否有房")privatebooleanhouse;//省略上述所有属性对应的getter与setter方法......}` |
| :--- | :--- |


```
   在这个类当中，可以看到每个属性都有一个名为Label的annotation，它是一个由URule提供的用来描述字段属性的annotation，这个描述的值，在生成变量时会自动写到变量的“标题”当中，这里的标题将会在规则中直接引用，让标题有意义，对于规则的清晰表达很有价值。

   我们这里这个类就在当前urule-console模块所在的项目当中，所以可以直接通过反射生成所有的属性，生成后的效果如下：
```

![](http://wiki.bsdn.org/download/attachments/75071567/var-list.png?version=2&modificationDate=1527734565000&api=v2&effects=border-simple,shadow-kn)

```
   可以看到上图中Label这个annotation对应的描述写入到变量的“标题”当中。

   在URule的服务器客户端模式下，我们的规则都是在服务器上定义的，这就有可能定义变量的时候变量分类对应的实体类在服务器上不存在，而只在客户端上存在，这种情况下就不能通过反射来生成对应的字段，这时我们可以在有这个实体类的客户端应用中通过URule中提供的com.bstek.urule.ClassUtils来生成目标实体类的xml描述文件，然后在到服务器上，点击变量分类“操作列”上中间那个上传图标将这个xml描述文件上传，同样可以生成对应的字段信息。使用ClassUtils类生成描述文件的代码如下所示：
```

**ClassUtils类使用方法**

| 1234 | `publicstaticvoidmain(String[] args) {File file=newFile("d:/customer.xml");ClassUtils.classToXml(Customer.class, file);}` |
| :--- | :--- |


```
   运行这个main方法，就会在D盘下生成一个customer.xml的实体类描述文件，再上传这个文件即可。
```

说明

在定义变量库文件时，对应的实体类不一定真实存在，同样，在运行规则时，如果发现对应的实体类不在当前JVM的classpath中时，引擎会使用一个名为GeneralEntity的类来代替这目标实现类运行。所以在URule的客户端服务器模式下，服务器上定义变量库时，对应的实体类一般都不在服务器上，而位于调用规则运行的客户端上，但对于服务器上规则定义与测试是没有影响的。

```
   这到里，变量库文件就定义好了，可以根据需要在一个文件中添加多个变量分类，相应对应到多个Java实体类。
```

变量名的重构

变量定义好了之后，会被其它类型的规则文件引用，如果后期变量需要需要修改，在URULE PRO版本中提供了变更名的重构功能。在上面的操作中我们可以看到，无论是变量的分类名称，还是具体的变量名在其操作列上都有一个![](http://wiki.bsdn.org/download/attachments/75071567/refactor.png?version=1&modificationDate=1527734727000&api=v2)图标，点击该图标就可以对当前行的变量名进行修改，这样就完成了变量名的重构。

在后面介绍的常量、参数、动作中，对于它们的名称的修改，URULE PRO版中同样提供重构功能的支持，这里不再赘述。

# 常量库文件 {#id-3.库文件介绍-常量库文件}

```
   前面说过，常量库文件中是用来定义枚举信息，选中我们的项目，在“库”节点上右键，创建一个常量库文件，如下图所示：
```

![](http://wiki.bsdn.org/download/attachments/75071567/constants.png?version=1&modificationDate=1475131088000&api=v2&effects=border-simple,shadow-kn)

```
   与变量库文件类似，常量也是由分类和具体的常量值构成，比如性别有男女之分，那么这里的“性别”就属性分类，“男”、“女”就属性具体的常量值。在常量的分类中，“名称”一般定义具体的分类名，“标题”是一段描述（比如“性别”是标题，“gender”是名称），同样这个“标题”也会出现在规则引用当中；加好分类后就可以添加这个分类下具体的常量值，常量值也有名称和标题之分，名称是具体的常量值，标题则是描述，比如“男”是标题，"true"是名称，同样“女”是标题，“false”是名称，如下图所示：
```

![](http://wiki.bsdn.org/download/attachments/75071567/c-def.png?version=1&modificationDate=1475131662000&api=v2&effects=border-simple,shadow-kn)

```
   同样，在一个变量库文件中可以根据需要添加多个变量分类。
```

常量值使用Spring中加载的properties文件值


URule是一款基于RETE算法纯Java的规则引擎产品。URule有两个不同版本：一个是基于Apache-2.0 License的开源版本；另一个是需要购买授权的PRO版本；URule PRO版完全兼容开源版本做出来的各种类型的规则文件。 在URule当中提供了向导式规则集、脚本式规则集、决策表、交叉决策表\\(PRO版\\)、决策树、评分卡及决策流共七种类型的规则定义方式，配合基于WEB的设计器，可快速实现规则的定义、维护与发布。 点击\[http://www.bstek.com\]\(http://www.bstek.com/\)了解更多关于URule PRO版信息；URule开源版本采用Apache-2.0开源协议，Github地址为：\[https://github.com/youseries/urule\]\(https://github.com/youseries/urule\)，欢迎前去fork、star。

|   |   | URULE PRO版与开源版主要功能比较 |
| :--- | :--- | :--- |
| 特性 | URULE PRO版 | URULE开源版 |
| 向导式决策集 | 有 | 有 |
| 脚本式决策集 | 有 | 有 |
| 决策树 | 有 | 有 |
| 决策流 | 有 | 有 |
| 决策表 | 有 | 有 |
| 交叉决策表 | 有 | 无 |
| 文件名、项目名重构 | 有 | 无 |
| 参数名、变量常量名重构 | 有 | 无 |
| 算法优化及性能调优 | 有 | 无 |
| 更为完善的文件读写权限控制 | 有 | 无 |
| 技术支持 | 有 | 无 |
| ...... |   |   |

```
   URule采用的是典型的客户端-服务器运行模式，URule的客户端是指那些需要使用规则引擎的应用，所有的Java应用都可以作为URule客户端（包含Web与非Web环境）；对于URule的服务端来说，则要求其必须是一个Java Web应用，它即可以以一个独立的Java Web应用运行，也可以嵌入到一个普通的Java Web应用当中运行，URule服务端可以实现规则的定义、维护与发布，所以这些操作，全部在浏览器中完成。URule客户端与服务器之间采用标准的HTTP协议进行通讯，通过HTTP，客户端既可以自动向服务器索取需要的最新的知识包，也可以是服务端在知识包更新时主动推送到客户端，对于服务器，每个规则项目都可以有多个客户端，同时服务器上知识包更新时可以主动推送到所有配置的客户端当中。


   URule2的控制台主界面如下图所示：
```

![](http://wiki.bsdn.org/download/attachments/75071499/main.png?version=1&modificationDate=1475047307000&api=v2&effects=border-simple,shadow-kn)

```
  在URule2的控制台当中，项目资源的展示方式，除了上图中看到的与原URule1风格一致的分类展示方式外，URule2还增加了不分类的列表型集中资源展示方式，如下图所示：
```

![](http://wiki.bsdn.org/download/attachments/75071499/main1.png?version=1&modificationDate=1475047635000&api=v2&effects=border-simple,shadow-kn)

```
   除此之外，URule2中还可以对项目进行过滤显示、对项目中资源类型进行过滤显示等，如下图所示：
```

![](http://wiki.bsdn.org/download/attachments/75071499/list1.png?version=1&modificationDate=1475047782000&api=v2&effects=border-simple,shadow-kn)![](http://wiki.bsdn.org/download/attachments/75071499/list2.png?version=1&modificationDate=1475047793000&api=v2&effects=border-simple,shadow-kn)

```
                            项目过滤                                                                                            资源文件类型过滤
```

## 向导式决策集

```
   一个向导式决策集里可以建多个普通规则或循环规则，如下图所示：
```

![](http://wiki.bsdn.org/download/attachments/75071499/click-ruleset.png?version=1&modificationDate=1475048915000&api=v2&effects=border-simple,shadow-kn)

## 脚本式决策集

```
   向导式决策集中可实现的功能，在脚本式决策集也可以实现，反之亦然，如下图所示：
```

![](http://wiki.bsdn.org/download/attachments/75071499/sc-ruleset.png?version=1&modificationDate=1475049133000&api=v2&effects=border-simple,shadow-kn)

## 决策表

```
   通过二维表来表现一组规则，URule中的决策表如下图所示：
```

![](http://wiki.bsdn.org/download/attachments/75071499/dt.png?version=2&modificationDate=1475049661000&api=v2&effects=border-simple,shadow-kn)

## 交叉决策表

```
   通过横向和纵向两个维度交叉来决定一个具体的值。URULE PRO中的交叉决策表可根据业务需要无限制的添加横向和纵向两个维度的层数和组数。
```

![](http://wiki.bsdn.org/download/attachments/75071499/crosstab.png?version=1&modificationDate=1527733881000&api=v2)

## 决策树

```
   以树形结构来表现特定类型的规则，在URule当中，为节省空间，决策树是一棵躺倒的树，如下图所示：
```

![](http://wiki.bsdn.org/download/attachments/75071499/tree.png?version=1&modificationDate=1475049899000&api=v2&effects=border-simple,shadow-kn)

## 评分卡

```
    评分卡在一些特定领域有着非常广泛的应用，URule2中的评分卡设计器如下图所示：
```

![](http://wiki.bsdn.org/download/attachments/75071499/card.png?version=1&modificationDate=1475050031000&api=v2&effects=border-simple,shadow-kn)

## 决策流

```
   用于规则编排作用的决策流，对于一个复杂的规则项目来说，是不可或缺的，URule2中的决策流设计器如下图所示：
```

![](http://wiki.bsdn.org/download/attachments/75071499/flow.png?version=1&modificationDate=1475050218000&api=v2&effects=border-simple,shadow-kn)

* No labels

* Powered by[Atlassian Confluence](#)5.0.1 ,[Team Collaboration Software](#)

* [Report a bug](#)
* [Atlassian N](#)




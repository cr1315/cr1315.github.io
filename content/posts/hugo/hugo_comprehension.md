---
title: "对Hugo的理解"
date: 2021-12-03T00:37:00+09:00
lastmod: 2022-01-27T23:22:00+09:00
---

# hugo页面组成的重要元素

## content

首先，自己的内容都要放在content folder底下，content底下的第一层作为type/section使用，一般是一个folder。  

- 这个folder里如果有index.md，则这是一个leaf bundle，也就是一个单一的页面。然后这个folder里可以放各种资源（resource），包括images，pdfs等等都可以，是这个leaf page独有的资源。
    - leaf bundle里不能再放leaf bundle
- 如果这个folder里有_index.md，则这是一个branch bundle，简单理解就是存放多个页面的文件夹。
    - 这个folder里可以放leaf bundle，也可以放branch bundle。嘛，扩展了的文件与文件夹的概念。

## layout

这个folder里放该怎么渲染页面，根据content的type/section来按照一定的优先级确定一个layout，按照其中的template把content里的markdown渲染成一个html页面。  
这可能是熟悉一些hugo之后第一个customize的东西吧，简单来说，控制了这两个folder的东西，至少就控制了页面的内容和展示这两个部分。至少我就算是在做网页了？


## archetypes

layout控制多了就会总结出一些经验，同一个type/section的页面总会有相似的结构，这就叫archetype。在这里定义一些自己用得顺手的archetype算是用熟了hugo之后的第一个进阶吧？

### hugo should always run at the site ROOT path

> added at `2022-01-27 23:14`

最近想加一个新command，叫`hugo new bundle`  
在archetypes里用folder的形式来做bundle的原型というか、templateというか  
然后用`hugo new bundle`命令来在当前path下做一个新的bundle，这里并不在乎是leaf bundle，还是branch bundle  
只是bundle template里的folder和文件都照着生成一份，然后像是`index.md`或`_index.md`这样的文件，再把里面的template string啥的执行一下替换掉  

想想还是挺有用的一个功能  
但是遇见了一个瓶颈，`hugo`的命令都得在site的根目录执行  
这样的话就只能在执行命令的时候把path传进去了  
但总感觉这样就有点不美了，与原设计有一个背离感

因为path对我来说非常重要，我想让sitebar能一定程度上反映src folder的结构  
或者说，我post摆放的结构就是按照最终出现在网站上的结构摆放的

这么一想，难道不应该是这样么？  
好像struts有struts-config，spring就更不用说了，直接在Java source里写annotation  
好像我知道的framework里就CodeIgniter是按照文件结构来组织网页的  
哦，不对还有Next.js  
嗯，不管怎么说，我还是喜欢这样子组织内容的方式  
更直观


## template

hugo用得越来越熟练，开始自定义更细致的东西了。  
不是单纯得去修改一个页面的模版，而是把页面上的内容模块化，就制作一个个小的template，目前还处于第一阶段，臆测是不是可以理解成React里的component呢，算是进阶级了吧。

### hugo is all about templates

> added at `2022-02-01T23:06`

最近看hugo的docs，重新读template的overview那一篇  
突然认识到，hugo的所有东西可以说都是围绕着这个template来展开的

当たり前だけど、なぜ今さらためて言うかというと  

之前可能是对hugo的理解太浅，  
重点放在content里面了，其中有一些会变的部分也基本在archetype和partial之类的了  
而template是因为太当たり前了么，反而没看见

那么具体来说，template指的是什么呢  
我又看到了什么呢这回

简单来说就一句话，上承接网站的外表，即呈现给user看的真正的页面  
下衔接content里的内容，然后从这里再接bundle和partial之下的东西  
正所谓是承上启下，非常重要的角色

如果想自定义自己的theme的话，这个template的存在就不得不深刻理解一下了

像是我想给每一个页面一个自定义css的机会，于是page bundle的archetype里总一个css的folder，里面总有一个css文件  
而这个css文件要给谁，让谁去用呢
就是template的事儿了

再比如我不想内容都组织到posts里的话，我想加一个section  
当然不加这个新section对应的template也不是不行
但是新section总是有点新的地方吧，要不然可能也不想加新section了  
而这新的部分该怎么实现呢，毫无疑问就是要定义它专属的template来实现的


## config

就目前能看到的东西来讲，这个可能是最深的了吧。  
真正开始配置hugo的运行，理解hugo内部的动作，让hugo按我想的方式运作。配合上述各种元素，真正做到如臂使指。  
嘛，到这个阶段再更新这篇文章吧。那时候应该能看到更多东西。


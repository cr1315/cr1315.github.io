---
title: "对Hugo的理解"
date: 2021-12-03T00:37:05+09:00
draft: true
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

## template

hugo用得越来越熟练，开始自定义更细致的东西了。  
不是单纯得去修改一个页面的模版，而是把页面上的内容模块化，就制作一个个小的template，目前还处于第一阶段，臆测是不是可以理解成React里的component呢，算是进阶级了吧。

## config

就目前能看到的东西来讲，这个可能是最深的了吧。  
真正开始配置hugo的运行，理解hugo内部的动作，让hugo按我想的方式运作。配合上述各种元素，真正做到如臂使指。  
嘛，到这个阶段再更新这篇文章吧。那时候应该能看到更多东西。
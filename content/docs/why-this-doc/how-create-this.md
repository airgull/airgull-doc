---
title: "这个站点是怎么做出来的？"
weitht: 3


---

使用 hugo 静态站点创建工作生成，同时使用了 docsy 主题。

## hugo简介及基本用法

## docsy 主题的使用方法

{{% alert title="提醒" %}}
> 发现一个有些html代码不渲染的问题，需要在配置文件中增加：
{{% /alert %}}
````toml
[markup.goldmark]
    [markup.goldmark.renderer]
      unsafe = true
````

> Page Bundles 的类型
- Leaf Bundle (leaf 意思是没有子节点，首页：index.md)
- Branch Bundle (首页：_index.md，包括：home page, section, taxonomy terms, taxonomy list)

### docsy 中的 shortcode

这个主题提供了一系列的 page block 短代码用于展示页和关于页面的制作

#### block/cover
  
提供了全屏页面，里面可以使用html对内部进行排版，内部内容会居于全屏的中心，并且可是使用如下参数设置其属性


| Parameter    | Default                        | Description                           |
| ------------ | ------------------------------ | ------------------------------------- |
| title        |                                | The main display title for the block. |
| image_anchor |                                |
| height       |                                | See above.                            |
| color        |                                | See above.                            |
| byline       | Byline text on featured image. |
  

#### blocks/lead

提供一个区域，带有向下指引的箭头，有两个属性高度和颜色

| Parameter | Default | Description |
| --------- | ------- | ----------- |
| height    |         | See above.  |
| color     |         | See above.  |


#### blocks/section

管理内容的，可以方便的做多列的排放

| Parameter | Default | Description                        |
| --------- | ------- | ---------------------------------- |
| height    |         | See above.                         |
| color     |         | See above.                         |
| type      |         | 里面放什么类型的 block，如 feature |


#### blocks/feature

描述每个对象的特性的html片段

| Parameter | Default | Description            |
| --------- | ------- | ---------------------- |
| title     |         | The title to use.      |
| url       |         | The URL to link to.    |
| icon      |         | The icon class to use. |

#### blocks/link-down

创建一个“下一个”导航链接

| Parameter | Default | Description |
| --------- | ------- | ----------- |
| color     | info    | See above.  |


#### alert

提示信息

| Parameter | Default | Description                                                   |
| --------- | ------- | ------------------------------------------------------------- |
| color     | primary | One of the theme colors, eg `primary`, `info`, `warning` etc. |

#### pageinfo

页面信息，可以给访问者一些提醒

{{% pageinfo color="primary" %}}
This is placeholder content
{{% /pageinfo %}}

| Parameter | Default | Description                                                   |
| --------- | ------- | ------------------------------------------------------------- |
| color     | primary | One of the theme colors, eg `primary`, `info`, `warning` etc. |




#### imgproc

The **imgproc** shortcode finds an image in the current [Page Bundle](/docs/adding-content/content/#page-bundles) and scales it given a set of processing instructions.


The example above has also a byline with photo attribution added. When using illustrations with a free license from [WikiMedia](https://commons.wikimedia.org/) and simlilar, you will in most situations need a way to attribute the author or licensor. You can add metadata to your page resources in the page front matter. The `byline` param is used by convention in this theme:


```` yaml
resources:
- src: "**spruce*.jpg"
  params:
    byline: "Photo: Bjørn Erik Pedersen / CC-BY-SA"
````


| Parameter | Description                                                             |
| --------: | ----------------------------------------------------------------------- |
|         1 | The image filename or enough of it to identify it (we do Glob matching) |
|         2 | Command. One of `Fit`, `Resize` or `Fill`.                              |
|         3 | Processing options, e.g. `400x450`.                                     |

#### swaggerui 

根据某些平台生成的 api 信息，json格式或yaml格式，使用 swaggerui 可以生成更友好的查看方式。

The `swaggerui` shortcode can be placed anywhere inside a page with the [`swagger` layout](https://github.com/google/docsy/tree/master/layouts/swagger); it renders [Swagger UI](https://swagger.io/tools/swagger-ui/) using any OpenAPI YAML or JSON file as source. This can be hosted anywhere you like, for example in your site's root [`/static` folder](/docs/adding-content/content/#adding-static-content).

```yaml
---
title: "Pet Store API"
type: swagger
weight: 1
description: Reference for the Pet Store API
---

{{</* swaggerui src="/openapi/petstore.yaml" */>}}
```


You can customize Swagger UI's look and feel by overriding Swagger's CSS or by editing and compiling a [Swagger UI dist](https://github.com/swagger-api/swagger-ui) yourself and replace `themes/docsy/static/css/swagger-ui.css`.



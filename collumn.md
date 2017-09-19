
## column 布局

|方法|参数|描述|
|---|---|---|
|column-width|px % em rem vw vh|单列宽度|
|column-count|flex-start flex-end center baseline stretch|列数|
|column-gap|px % em rem vw vh|间隔宽度|

|方法|参数|描述|
|---|---|---|
|column-rule|row row-reverse column column-reverse|父极 主轴方向|
|column-fill|balance auto|列高|
|column-rule-color|/|父极主轴方向 换行|
|column-rule-style|flex-start flex-end center space-between space-around|子极 副轴 个体对齐方式|
|column-rule-width|number 默认0|子极 位置|
|column-span|number 默认0|子极 空间有余时 放大比例|
|columns|number 默认1|子极 空间不足时 缩小比例|
|break-after|length:px em rem % vh vw|子极 分配空余空间的定宽|
|break-before|length:px em rem % vh vw|子极 分配空余空间的定宽|
|break-inside|length:px em rem % vh vw|子极 分配空余空间的定宽|

## 网格布局 grid
类似table的布局但不需要改动html


给父容器的display属性设置为grid或者inline-grid来定义一个网格。这样你就可以使用grid-template-columns和grid-template-rows属性来创建一个网格。

|方法|参数|描述|
|---|---|---|
|grid-template-columns|px % em rem vw vh(多个宽度)|定义宽度|
|grid-template-rows|px % em rem vw vh(多个宽度)|定义行高|
|grid-auto-columns|flex-start flex-end center baseline stretch|自动列宽|
|grid-auto-columns|flex-start flex-end center baseline stretch|自动行高|
|grid-auto-columns|flex-start flex-end center baseline stretch|列数|
|grid-auto-columns|flex-start flex-end center baseline stretch|列数|
|grid|px % em rem vw vh|单列宽度|
|grid-template|flex-start flex-end center baseline stretch|列数|




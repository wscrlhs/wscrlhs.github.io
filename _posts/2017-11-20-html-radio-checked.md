---
layout: post
title: thinkphp radio标签保持选中状态 
categories: [thinkphp]
tags: thinkphp radio
---

* content
{:toc}

<h3>代码</h3>

```html
<input type="radio" name="status" value="0" >
<input type="radio" name="status" value="1" >
<input type="radio" name="status" value="3" >
```

1. 使用模版引擎提供的比较标签

```html
<input type="radio" name="status" value="0" <eq name="status" value="0">checked="checked"</eq> >
<input type="radio" name="status" value="1" <eq name="status" value="1">checked="checked"</eq> >
<input type="radio" name="status" value="2" <eq name="status" value="2">checked="checked"</eq> >
```

2. 使用thinkphp的IF标签

```html
<if condition="I('status') eq '0'">
   <input type="radio" checked="checked" name="status" value="0">
     <else />
    <input type="radio" name="status" value="0">
     </if>
 <if condition="I('status') eq '1'">
      <input type="radio" checked="checked" name="status" value="1">
       <else />
     <input type="radio" name="status" value="1">
</if>
```

3. 使用javascript

```javascript
<SCRIPT LANGUAGE="JavaScript">
$("input:radio[name='status']").eq({:I('status')}).attr("checked",true);
</SCRIPT>
```

4. 使用内嵌php标签

```html
<input type="radio" name="status" value="0" <?php if(I('status')==0):?> checked="checked"<?php endif;?>>
<input type="radio" name="status" value="1" <?php if(I('status')==2):?> checked="checked"<?php endif;?>>
<input type="radio" name="status" value="2" <?php if(I('status')==1):?> checked="checked"<?php endif;?>>
```


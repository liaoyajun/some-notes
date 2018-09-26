[TOC]
# **API 接口**
### **createCanvasContext**
#### 创建 canvas 绘图上下文(指定 canvasId)。需要指定 canvasId，该绘图上下文只作用于对应的&lt;canvas/&gt;。
``` JavaScript
const ctx = wx.createCanvasContext('myCanvas')
```
<br>
### **canvasToTempFilePath**
#### 把当前画布指定区域的内容导出生成指定大小的图片，并返回文件路径。
``` JavaScript
wx.canvasToTempFilePath({
  x: 100,
  y: 200,
  width: 50,
  height: 50,
  destWidth: 100,
  destHeight: 100,
  canvasId: 'myCanvas',
  success: function(res) {
    console.log(res.tempFilePath)
  }
})
```
<br>
# **context 对象的方法列表**
## **颜色，样式，阴影**
### **setFillStyle**
#### 设置填充色。如果没有设置 fillStyle，默认颜色为 black。
``` JavaScript
const ctx = wx.createCanvasContext('myCanvas')
ctx.setFillStyle('red')
ctx.fillRect(10, 10, 150, 75)
ctx.draw()
```
![setFillStyle](https://mp.weixin.qq.com/debug/wxadoc/dev/image/canvas/fill-rect.png?t=201798 "setFillStyle")
<br>
### **setStrokeStyle**
#### 设置边框颜色。如果没有设置 strokeStyle，默认颜色为 black。
``` JavaScript
const ctx = wx.createCanvasContext('myCanvas')
ctx.setStrokeStyle('red')
ctx.strokeRect(10, 10, 150, 75)
ctx.draw()
```
![setStrokeStyle](https://mp.weixin.qq.com/debug/wxadoc/dev/image/canvas/stroke-rect.png?t=201798 "setStrokeStyle")
<br>
### **setShadow**
#### 设置阴影样式。如果没有设置，offsetX 默认值为0， offsetY 默认值为0， blur 默认值为0，color 默认值为 black。
``` JavaScript
const ctx = wx.createCanvasContext('myCanvas')
ctx.setFillStyle('red')
ctx.setShadow(10, 50, 50, 'blue')
ctx.fillRect(10, 10, 150, 75)
ctx.draw()
```
![setShadow](https://mp.weixin.qq.com/debug/wxadoc/dev/image/canvas/shadow.png?t=201798 "setShadow")
<br>
## **渐变**
### **createLinearGradient**
#### 创建一个线性的渐变颜色。需要使用 addColorStop() 来指定渐变点，至少要两个。
``` JavaScript
const ctx = wx.createCanvasContext('myCanvas')

// Create linear gradient
const grd = ctx.createLinearGradient(0, 0, 200, 0)
grd.addColorStop(0, 'red')
grd.addColorStop(1, 'white')

// Fill with gradient
ctx.setFillStyle(grd)
ctx.fillRect(10, 10, 150, 80)
ctx.draw()
```
![createLinearGradient](https://mp.weixin.qq.com/debug/wxadoc/dev/image/canvas/linear-gradient.png?t=201798 "createLinearGradient")
<br>
### **createCircularGradient**
#### 创建一个圆形的渐变颜色。起点在圆心，终点在圆环。需要使用 addColorStop() 来指定渐变点，至少要两个。
``` JavaScript
const ctx = wx.createCanvasContext('myCanvas')

// Create circular gradient
const grd = ctx.createCircularGradient(75, 50, 50)
grd.addColorStop(0, 'red')
grd.addColorStop(1, 'white')

// Fill with gradient
ctx.setFillStyle(grd)
ctx.fillRect(10, 10, 150, 80)
ctx.draw()
```
![createCircularGradient](https://mp.weixin.qq.com/debug/wxadoc/dev/image/canvas/circular-gradient.png?t=201798 "createCircularGradient")
<br>
### **addColorStop**
#### 创建一个颜色的渐变点。小于最小 stop 的部分会按最小 stop 的 color 来渲染，大于最大 stop 的部分会按最大 stop 的 color 来渲染。需要使用 addColorStop() 来指定渐变点，至少要两个。
``` JavaScript
const ctx = wx.createCanvasContext('myCanvas')

// Create circular gradient
const grd = ctx.createLinearGradient(30, 10, 120, 10)
grd.addColorStop(0, 'red')
grd.addColorStop(0.16, 'orange')
grd.addColorStop(0.33, 'yellow')
grd.addColorStop(0.5, 'green')
grd.addColorStop(0.66, 'cyan')
grd.addColorStop(0.83, 'blue')
grd.addColorStop(1, 'purple')

// Fill with gradient
ctx.setFillStyle(grd)
ctx.fillRect(10, 10, 150, 80)
ctx.draw()
```
![addColorStop](https://mp.weixin.qq.com/debug/wxadoc/dev/image/canvas/color-stop.png?t=201798 "addColorStop")
<br>
## **线条样式**
### **setLineWidth**
#### 设置线条的宽度。
``` JavaScript
const ctx = wx.createCanvasContext('myCanvas')
ctx.beginPath()
ctx.moveTo(10, 10)
ctx.lineTo(150, 10)
ctx.stroke()

ctx.beginPath()
ctx.setLineWidth(5)
ctx.moveTo(10, 30)
ctx.lineTo(150, 30)
ctx.stroke()

ctx.beginPath()
ctx.setLineWidth(10)
ctx.moveTo(10, 50)
ctx.lineTo(150, 50)
ctx.stroke()

ctx.beginPath()
ctx.setLineWidth(15)
ctx.moveTo(10, 70)
ctx.lineTo(150, 70)
ctx.stroke()

ctx.draw()
```
![setLineWidth](https://mp.weixin.qq.com/debug/wxadoc/dev/image/canvas/line-width.png?t=201798 "setLineWidth")
<br>
### **setLineCap**
#### 设置线条的端点样式。
``` JavaScript
const ctx = wx.createCanvasContext('myCanvas')
ctx.beginPath()
ctx.moveTo(10, 10)
ctx.lineTo(150, 10)
ctx.stroke()

ctx.beginPath()
ctx.setLineCap('butt')
ctx.setLineWidth(10)
ctx.moveTo(10, 30)
ctx.lineTo(150, 30)
ctx.stroke()

ctx.beginPath()
ctx.setLineCap('round')
ctx.setLineWidth(10)
ctx.moveTo(10, 50)
ctx.lineTo(150, 50)
ctx.stroke()

ctx.beginPath()
ctx.setLineCap('square')
ctx.setLineWidth(10)
ctx.moveTo(10, 70)
ctx.lineTo(150, 70)
ctx.stroke()

ctx.draw()
```
![setLineCap](https://mp.weixin.qq.com/debug/wxadoc/dev/image/canvas/line-cap.png?t=201798 "setLineCap")
<br>
### **setLineJoin**
#### 设置线条的交点样式。
``` JavaScript
const ctx = wx.createCanvasContext('myCanvas')
ctx.beginPath()
ctx.moveTo(10, 10)
ctx.lineTo(100, 50)
ctx.lineTo(10, 90)
ctx.stroke()

ctx.beginPath()
ctx.setLineJoin('bevel')
ctx.setLineWidth(10)
ctx.moveTo(50, 10)
ctx.lineTo(140, 50)
ctx.lineTo(50, 90)
ctx.stroke()

ctx.beginPath()
ctx.setLineJoin('round')
ctx.setLineWidth(10)
ctx.moveTo(90, 10)
ctx.lineTo(180, 50)
ctx.lineTo(90, 90)
ctx.stroke()

ctx.beginPath()
ctx.setLineJoin('miter')
ctx.setLineWidth(10)
ctx.moveTo(130, 10)
ctx.lineTo(220, 50)
ctx.lineTo(130, 90)
ctx.stroke()

ctx.draw()
```
![setLineJoin](https://mp.weixin.qq.com/debug/wxadoc/dev/image/canvas/line-join.png?t=201798 "setLineJoin")
<br>
### **setMiterLimit**
#### 设置最大斜接长度，斜接长度指的是在两条线交汇处内角和外角之间的距离。 当 setLineJoin() 为 miter 时才有效。超过最大倾斜长度的，连接处将以 lineJoin 为 bevel 来显示
``` JavaScript
const ctx = wx.createCanvasContext('myCanvas')
ctx.beginPath()
ctx.setLineWidth(10)
ctx.setLineJoin('miter')
ctx.setMiterLimit(1)
ctx.moveTo(10, 10)
ctx.lineTo(100, 50)
ctx.lineTo(10, 90)
ctx.stroke()

ctx.beginPath()
ctx.setLineWidth(10)
ctx.setLineJoin('miter')
ctx.setMiterLimit(2)
ctx.moveTo(50, 10)
ctx.lineTo(140, 50)
ctx.lineTo(50, 90)
ctx.stroke()

ctx.beginPath()
ctx.setLineWidth(10)
ctx.setLineJoin('miter')
ctx.setMiterLimit(3)
ctx.moveTo(90, 10)
ctx.lineTo(180, 50)
ctx.lineTo(90, 90)
ctx.stroke()

ctx.beginPath()
ctx.setLineWidth(10)
ctx.setLineJoin('miter')
ctx.setMiterLimit(4)
ctx.moveTo(130, 10)
ctx.lineTo(220, 50)
ctx.lineTo(130, 90)
ctx.stroke()

ctx.draw()
```
![setMiterLimit](https://mp.weixin.qq.com/debug/wxadoc/dev/image/canvas/miter-limit.png?t=201798 "setMiterLimit")
<br>
## **矩形**
### **rect**
#### 创建一个矩形。fill() 或者 stroke() 方法将矩形真正的画到 canvas 中。
``` JavaScript
const ctx = wx.createCanvasContext('myCanvas')
ctx.rect(10, 10, 150, 75)
ctx.setFillStyle('red')
ctx.fill()
ctx.draw()
```
![rect](https://mp.weixin.qq.com/debug/wxadoc/dev/image/canvas/fill-rect.png?t=201798 "rect")
<br>
### **fillRect**
#### 填充一个矩形。用 setFillStyle() 设置矩形的填充色，如果没设置默认是黑色。
``` JavaScript
const ctx = wx.createCanvasContext('myCanvas')
ctx.setFillStyle('red')
ctx.fillRect(10, 10, 150, 75)
ctx.draw()
```
![fillRect](https://mp.weixin.qq.com/debug/wxadoc/dev/image/canvas/fill-rect.png?t=201798 "fillRect")
<br>
### **strokeRect**
#### 画一个矩形(非填充)。用 setStrokeStyle() 设置矩形线条的颜色，如果没设置默认是黑色。
``` JavaScript
const ctx = wx.createCanvasContext('myCanvas')
ctx.setStrokeStyle('red')
ctx.strokeRect(10, 10, 150, 75)
ctx.draw()
```
![strokeRect](https://mp.weixin.qq.com/debug/wxadoc/dev/image/canvas/stroke-rect.png?t=201798 "strokeRect")
<br>
### **clearRect**
#### 清除画布上在该矩形区域内的内容。clearRect 并非画一个白色的矩形在地址区域，而是清空，为了有直观感受，对 canvas 加了一层背景色。
``` JavaScript
const ctx = wx.createCanvasContext('myCanvas')
ctx.setFillStyle('red')
ctx.fillRect(0, 0, 150, 200)
ctx.setFillStyle('blue')
ctx.fillRect(150, 0, 150, 200)
ctx.clearRect(10, 10, 150, 75)
ctx.draw()
```
![clearRect](https://mp.weixin.qq.com/debug/wxadoc/dev/image/canvas/clear-rect.png?t=201798 "clearRect")
<br>
## **路径**
### **fill**
#### 对当前路径中的内容进行填充。默认的填充色为黑色。如果当前路径没有闭合，fill() 方法会将起点和终点进行连接，然后填充，详情见例一。fill() 填充的的路径是从 beginPath() 开始计算，但是不会将 fillRect() 包含进去，详情见例二。
``` JavaScript
const ctx = wx.createCanvasContext('myCanvas')
ctx.moveTo(10, 10)
ctx.lineTo(100, 10)
ctx.lineTo(100, 100)
ctx.fill()
ctx.draw()
```
![fill](https://mp.weixin.qq.com/debug/wxadoc/dev/image/canvas/fill-line.png?t=201798 "fill")
``` JavaScript
const ctx = wx.createCanvasContext('myCanvas')
// begin path
ctx.rect(10, 10, 100, 30)
ctx.setFillStyle('yellow')
ctx.fill()

// begin another path
ctx.beginPath()
ctx.rect(10, 40, 100, 30)

// only fill this rect, not in current path
ctx.setFillStyle('blue')
ctx.fillRect(10, 70, 100, 30)

ctx.rect(10, 100, 100, 30)

// it will fill current path
ctx.setFillStyle('red')
ctx.fill()
ctx.draw()
```
![fill](https://mp.weixin.qq.com/debug/wxadoc/dev/image/canvas/fill-path.png?t=201798 "fill")
<br>
### **stroke**
#### 画出当前路径的边框。默认颜色色为黑色。stroke() 描绘的的路径是从 beginPath() 开始计算，但是不会将 strokeRect() 包含进去，详情见例二。
``` JavaScript
const ctx = wx.createCanvasContext('myCanvas')
ctx.moveTo(10, 10)
ctx.lineTo(100, 10)
ctx.lineTo(100, 100)
ctx.stroke()
ctx.draw()
```
![stroke](https://mp.weixin.qq.com/debug/wxadoc/dev/image/canvas/stroke-line.png?t=201798 "stroke")
``` JavaScript
const ctx = wx.createCanvasContext('myCanvas')
// begin path
ctx.rect(10, 10, 100, 30)
ctx.setStrokeStyle('yellow')
ctx.stroke()

// begin another path
ctx.beginPath()
ctx.rect(10, 40, 100, 30)

// only stoke this rect, not in current path
ctx.setStrokeStyle('blue')
ctx.strokeRect(10, 70, 100, 30)

ctx.rect(10, 100, 100, 30)

// it will stroke current path
ctx.setStrokeStyle('red')
ctx.stroke()
ctx.draw()
```
![stroke](https://mp.weixin.qq.com/debug/wxadoc/dev/image/canvas/stroke-path.png?t=201798 "stroke")
<br>
### **beginPath**
#### 开始创建一个路径，需要调用fill或者stroke才会使用路径进行填充或描边。在最开始的时候相当于调用了一次 beginPath()。同一个路径内的多次setFillStyle()、setStrokeStyle()、setLineWidth()等设置，以最后一次设置为准。
``` JavaScript
const ctx = wx.createCanvasContext('myCanvas')
// begin path
ctx.rect(10, 10, 100, 30)
ctx.setFillStyle('yellow')
ctx.fill()

// begin another path
ctx.beginPath()
ctx.rect(10, 40, 100, 30)

// only fill this rect, not in current path
ctx.setFillStyle('blue')
ctx.fillRect(10, 70, 100, 30)

ctx.rect(10, 100, 100, 30)

// it will fill current path
ctx.setFillStyle('red')
ctx.fill()
ctx.draw()
```
![beginPath](https://mp.weixin.qq.com/debug/wxadoc/dev/image/canvas/fill-path.png?t=201798 "beginPath")

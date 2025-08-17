# 基础绘制

- 矩形

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Document</title>
  </head>
  <body>
    <canvas id="c1" width="600" height="400"></canvas>

    <script>
      const c1 = document.getElementById('c1');
      // 获取画笔 上下文对象
      const ctx = c1.getContext('2d');
      // 画矩形 fillRext(x, y, width, height)
      // ctx.fillRect(100, 200, 300, 300);

      ctx.beginPath(); // 开始绘制新路径
      ctx.rect(100, 100, 200, 100); // 添加一个矩形到当前路径，从 x 100 y 100 位置开始绘制， width 200 height 100
      ctx.stroke(); //绘制路径
      ctx.closePath(); // 结束路径

      ctx.beginPath();
      ctx.rect(200, 150, 200, 100);
      ctx.fill(); // 填充当前路径
      ctx.closePath();

      let height = 0;
      let timer = setInterval(() => {
        height++;
        ctx.clearRect(0, 0, c1.clientWidth, height);
        if (height > c1.clientHeight) {
          clearInterval(timer);
        }
      }, 10);
    </script>
  </body>
</html>
```

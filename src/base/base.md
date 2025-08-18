# 基础绘制

- 画矩形

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
      // 画矩形 fillRext(x, y, width, height) 填充模式
      // ctx.fillRect(100, 200, 300, 300);
      // 画矩形路径 strokeRect(x, y, width, height) 路径模式
      // ctx.strokeRect(100, 200, 300, 300);

      // 下面的写法是 fillRect 和 strokeRect 的分解写法

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

- 画圆弧

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

      // 画圆弧 ctx.arc(圆心x, 圆心y, 半径, 开始的角度, 结束的角度, （可选参数）顺时针画还是逆时针画) 默认值是 false 顺时针，true 为逆时针
      // 为什么 Math.PI （3.1415926） 是 180度？
      // 弧度制中，1弧度对应的角度为‌180/π度‌。由于π约等于3.14159，因此1弧度约等于57.2958度。当π弧度（即3.14159弧度）转换为角度时，计算为：‌3.14159 × 180/π ≈ 180度‌
      ctx.beginPath();
      ctx.arc(300, 200, 50, 0, Math.PI);
      // ctx.fill() 填充圆弧
      ctx.stroke(); // 路径模式
      ctx.closePath();

      // 画一张笑脸，每一笔都单独画一个完整的路径的写法，比较麻烦，相当于每画一个路径都要抬起画笔，然后再画新的路径
      // // 脸
      // ctx.beginPath();
      // ctx.arc(75, 75, 50, 0, Math.PI * 2);
      // ctx.stroke();
      // ctx.closePath();

      // // 左眼
      // ctx.beginPath();
      // ctx.arc(60, 65, 5, 0, Math.PI * 2);
      // ctx.stroke();
      // ctx.closePath();

      // // 右眼
      // ctx.beginPath();
      // ctx.arc(90, 65, 5, 0, Math.PI * 2);
      // ctx.stroke();
      // ctx.closePath();

      // // 嘴巴
      // ctx.beginPath();
      // ctx.arc(75, 75, 35, 0, Math.PI);
      // ctx.stroke();
      // ctx.closePath();

      // moveTo 绘制子路径，不连续的路径，相当于画笔移动到下一个位置
      // 脸
      ctx.beginPath();

      ctx.arc(75, 75, 50, 0, Math.PI * 2);

      // 可以发现圆形都是从圆的最右边的中点作为起始位置开始画的，所以都移动到下一个圆形的最右边的中点
      ctx.moveTo(65, 65);
      // 左眼
      ctx.arc(60, 65, 5, 0, Math.PI * 2);

      ctx.moveTo(95, 65);
      // 右眼
      ctx.arc(90, 65, 5, 0, Math.PI * 2);

      ctx.moveTo(110, 75);
      // 嘴巴
      ctx.arc(75, 75, 35, 0, Math.PI);

      ctx.stroke();
      ctx.closePath();
    </script>
  </body>
</html>
```

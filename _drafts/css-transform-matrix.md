---
layout: post
tags:
  - web
  - css
  - transform
  - animation
category: note
title: CSS transform 旋轉
---

### 講點幹話

因為參加黑客社幹訓要做個網頁，所以就做了個動畫效果，還一個做到凌晨三點。

果然不該拿毒品做的 (?。

就這樣用三層動畫做出來了。

![たのしー](https://i.imgur.com/TbDqutt.gif)

([東西放這邊](/workshop/serval_cat.html))

<br>
<br>

中間還因為 Firefox 和 Chrome 在套用 transform 裡面多個 rotate 時的行為差異

害我不能用 rotateX rotateY rotateZ 這三個直接填選轉角度的來兜旋轉就好。

要用 rotate3d 在那邊算三個角度兜起來會有啥效果(´Ａ｀。)。

<br>
<br>

然後隔天聽到說要做 RWD。

<p class="intensify">
_(´ཀ`」 ∠)_ 
<br>
<strong>在這邊插入一張生無可戀的臉</strong>
</p>

<br>
<br>

反正都開了頭了那就來弄吧ヽ(✿ﾟ▽ﾟ)ノ 。

而且因為橫向的時候跑橫的，那直向的時候就來跑直的吧ヽ(✿ﾟ▽ﾟ)ノ #顯示為放棄治療。

<br>
<br>

既然是要跑直的，就代表說要多轉個九十度。

然後右上角的就不聽話了

別人都跑直的，他偏偏跑橫的

而且角度怎麼算怎麽不對 (好啦我懶得認真算啦)

<br>
<br>

在看著 [MDN 的 rotate3d 文件](https://developer.mozilla.org/en-US/docs/Web/CSS/transform-function/rotate3d)時

看著那個轉換矩陣覺得絕望開始亂看 transform 底下的函式的時候。

看到了[這個](https://developer.mozilla.org/en-US/docs/Web/CSS/transform-function/matrix)

<br>
<br>

<p class="intensify">
既然沒辦法讓瀏覽器算出自己要的轉換矩陣那就自己弄嘛
</p>
(完全不構成逃避的逃避)

<br>
<br>

```css
transform: matrix(a,b,c,d,tx,ty);
```
<br>

基本上上面這條的操作跟下面這個算式等價。

\\( a, b, c, d \\) 是變換矩陣的元素

\\( tx, ty \\) 就是轉換完的位移量

<p>
\[
\begin{bmatrix} x \\ y \end{bmatrix} = \begin{bmatrix} a & c \\ b & d \end{bmatrix} \begin{bmatrix} ix \\ iy \end{bmatrix} + \begin{bmatrix} tx \\ ty \end{bmatrix}
\]
</p>

<br>
<br>

經過~~大量試誤~~精密的計算之後得出了這個！

<br>

![モバイルもたのしー](https://i.imgur.com/v4fIRfh.gif)

(會跳動一下是正常的 因為我錄影時間沒算很好)

<br>
<br>

轉來轉去都快弄不懂到底哪邊是 x 哪邊是 y 了 (抹臉

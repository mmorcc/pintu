# PuzzleView
Android拼图支持库，想法来自Layout for Instagram。

2.0发布了，支持超级酷炫的斜线拼图，圆角模式

英文[README](https://github.com/wuapnjie/PuzzleView/blob/master/README.md)

### Demo
效果看视频

[点击观看Youtube](https://www.youtube.com/watch?v=jfOJCh-uDIo)
</br>
[点击观看Youku](http://v.youku.com/v_show/id_XMTY5Nzk3NTYyMA==.html?beta&)


![](https://github.com/wuapnjie/PuzzleView/blob/master/screenshots/screenshot1.png)
![](https://github.com/wuapnjie/PuzzleView/blob/master/screenshots/screenshot2.png)

**现在支持斜线模式和圆角拼图了**
</br>
</br>
![](https://github.com/wuapnjie/PuzzleView/blob/master/screenshots/screenshot4.png)

### 使用
在build.gradle添加，当然你也可以直接导入library module，方便修改。
```gradle
compile 'com.flying.xiaopo:puzzle:2.0.0-alpha'
```

在xml布局中
```xml
 <com.xiaopo.flying.puzzle.PuzzleView
        android:id="@+id/puzzle"
        android:layout_width="match_parent"
        android:layout_height="match_parent" />
        
 <com.xiaopo.flying.puzzle.SquarePuzzleView
        android:id="@+id/square_puzzle"
        android:layout_width="match_parent"
        android:layout_height="match_parent" />
```

在Java代码中, 可以更改一些PuzzleView的属性，比如选中边框的颜色之类的属性。
```java
puzzleView.setPuzzleLayout(puzzleLayout);
puzzleView.setTouchEnable(true);
puzzleView.setNeedDrawLine(false);
puzzleView.setNeedDrawOuterLine(false);
puzzleView.setLineSize(4);
puzzleView.setLineColor(Color.BLACK);
puzzleView.setSelectedLineColor(Color.BLACK);
puzzleView.setHandleBarColor(Color.BLACK);
puzzleView.setAnimateDuration(300);
```
控制一些图形的变换，旋转，镜像，翻转，画边框，替换。
```java
mPuzzleView.rotate(90f);
puzzleView.flipHorizontally();
puzzleView.flipVertically();
puzzleView.setLineSize(currentDegrees);
puzzleView.setPieceRadian(currentDegrees);
puzzleView.setNeedDrawLine(!mPuzzleView.isNeedDrawLine());
puzzleView.replace(bitmap);
```

当然更快的了解方式还是看demo的源码，额，这个demo写的有点急，如果代码不是很好看的话，请原谅我。

### 布局
PuzzleView取决于PuzzleLayout，当然我们可以自定义PuzzleLayout
</br>
如果你不想自定义PuzzleLayout，该库中也内置了许多Layout样式，理论上Instagram Layout中的样式都有，没有你也可以自己写。
</br>
在这个demo中有个Playground页面，上面展示了所有的内置Layout样式，你可以点击查看效果，demo中自带了几张图。
![](https://github.com/wuapnjie/PuzzleView/blob/master/screenshots/screenshot3.png)

### 自定义布局
自定义PuzzleLayout也非常简单. 只要继承PuzzleLayout并重写layout()方法就好了。
</br>
在PuzzleLayout类中自带了几个方便布局的方法，只要灵活组合应用就可以打造各种各样的布局。比如像下面这样。
```java
public class CustomLayout extends PuzzleLayout {

    @Override
    public void layout() {
        addLine(getOuterBorder(), Line.Direction.HORIZONTAL, 1f / 2);
        addLine(getBorder(0), Line.Direction.VERTICAL, 1f / 2);
    }
}
```

这个布局就是，先添加了一条横线在最外面的Border的1/2处，之后Border会被这条线分为两个Border，
然后又在第一个Border的1/2处添加了一条竖线，于是这个布局就被分割为3个Border，可以放三张图片。

当然可以看内置的Layout怎么编写从而学习

![](https://github.com/wuapnjie/PuzzleView/blob/master/screenshots/puzzle.png)

### 最后
看几张效果图
[Click here](http://weibo.com/5350471787/E54jjxzlI)

### 更新
* **2017/08/29**  2.0.0-alpha add slant mode puzzle, and to support round cornors
* **2017/04/15**  1.1.1 add piece select listener
* **2017/02/15**  1.1.0 add piece padding function 
### License

    Copyright 2016 wuapnjie

    Licensed under the Apache License, Version 2.0 (the "License");
    you may not use this file except in compliance with the License.
    You may obtain a copy of the License at

       http://www.apache.org/licenses/LICENSE-2.0

    Unless required by applicable law or agreed to in writing, software
    distributed under the License is distributed on an "AS IS" BASIS,
    WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
    See the License for the specific language governing permissions and
    limitations under the License.



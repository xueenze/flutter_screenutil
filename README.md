
# flutter_ScreenUtil
**flutter 屏幕适配方案**

github: https://github.com/lizhuoyuan/flutter_ScreenUtil </br>
csdn博客工具介绍:https://blog.csdn.net/u011272795/article/details/82795477


## 使用方法:

### 安装依赖：
```
dependencies:
  flutter:
    sdk: flutter
  # 添加依赖
  flutter_screenutil:
    git:
      url: git://github.com/lizhuoyuan/flutter_ScreenUtil
```

### 在每个使用的地方导入包：
```
import 'package:flutter_screenutil/flutter_screenutil.dart';

```

### 初始化设置尺寸
在使用之前请设置好设计稿的宽度和高度，传入设计稿的宽度和高度(单位px)
如果不设置则使用默认尺寸，默认为1080*1920
推荐在项目入口中设置，以保证在每次使用之前设置好了适配尺寸:

```
ScreenUtil.instance = new ScreenUtil(width: 360, height: 720);
```

### 使用：

适配尺寸：
```
//传入设计稿的px尺寸：
width: ScreenUtil().setWidth(540),
height: ScreenUtil().setHeight(200),
```

其他相关api：
```
    ScreenUtil.pixelRatio       //设备的像素密度
    ScreenUtil.screenWidth    //设备宽度
    ScreenUtil.screenHeight    //设备高度
    ScreenUtil.bottomBarHeight //底部安全区距离，适用于全面屏下面有按键的
    ScreenUtil.statusBarHeight //状态栏高度 刘海屏会更高  单位px

    ScreenUtil().scaleWidth //宽度相对于设计稿放大的倍数
    ScreenUtil().scaleHeight //高度相对于设计稿放大的倍数

```

```
import 'package:flutter_app/ScreenUtil.dart';  //导入

@override
  Widget build(BuildContext context) { 
   
 print(ScreenUtil().setWidth(180));
    print('设备的像素密度:${ScreenUtil.pixelRatio}'); //设备的像素密度
    print('设备宽度:${ScreenUtil.screenWidth}'); //设备宽度
    print('设备高度:${ScreenUtil.screenHeight}'); //设备高度
    print('底部安全区距离:${ScreenUtil.bottomBarHeight}'); //底部安全区距离，适用于全面屏下面有按键的
    print('状态栏高度:${ScreenUtil.statusBarHeight}px'); //状态栏高度 刘海屏会更高

    print('宽度相对于设计稿放大的倍数:${ScreenUtil().scaleWidth}'); //宽度相对于设计稿放大的倍数
    print('高度相对于设计稿放大的倍数:${ScreenUtil().scaleHeight}'); //高度相对于设计稿放大的倍数
    return new Scaffold(
      appBar: new AppBar(
        title: new Text(widget.title),
      ),
     body: new Center(
        child: Column(
          children: <Widget>[
            Row(
              children: <Widget>[
                Container(
                  width: ScreenUtil().setWidth(375),
                  height: ScreenUtil().setHeight(200),
                  color: Colors.red,
                  child: Text(ScreenUtil().setWidth(375).toString()),
                ),
                Container(
                  width: ScreenUtil().setWidth(375),
                  height: ScreenUtil().setHeight(200),
                  color: Colors.blue,
                  child: Text(ScreenUtil().setWidth(375).toString()),
                ),
              ],
            ),
            Text(ScreenUtil.screenWidth.toString()),
            Text(ScreenUtil.screenHeight.toString()),
          ],
      ),
    );
  }
```

### 使用示例:

[example demo](/example)
 
效果:
上面的205.xxx 是dp的单位,
下面的单位是px

![效果](微信图片_20180921000611.png)


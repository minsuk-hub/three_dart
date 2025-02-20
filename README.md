# 설치 가이드
https://pub.dev/packages/flutter_gl/install

https://pub.dev/packages/three_dart/install


# flutter_gl
## import문
```
import 'package:flutter_gl/flutter_gl.dart';
```

## gl 사용법
```
int width = 200;
int height = 200;
num dpr = 1.0;

flutterGlPlugin = FlutterGlPlugin();

Map<String, dynamic> _options = {
    "width": width, 
    "height": height, 
    "dpr": dpr,
    "antialias": true,
    "alpha": false
};    
await flutterGlPlugin.initialize(options: _options);

// on web this need called after web canvas dom was added to document
await flutterGlPlugin.prepareContext();

// you can get gl by
gl = flutterGlPlugin.gl;

// then you can call OpenGL ES API by gl like
gl.clearColor(0.0, 0.0, 0.0, 1.0);
gl.clear(gl.COLOR_BUFFER_BIT);

// use this method to notify Flutter update Texture Widget
// sourceTextue is a texture which bind to FBO framebuffer
flutterGlPlugin.updateTexture(sourceTexture);
```

## open gl context를 플러터와 공유하기

## 안드로이드
when init the plugin, save share opengl context with ThreeEgl,
```
ThreeEgl.setContext("shareContext", shareEglEnv.eglContext);
```


so you can get it use ThreeEgl lib, then create yourself opengl context share with "shareContext"
```
shareContext = ThreeEgl.getContext("shareContext");
```

## IOS
for iOS the key is 3 ...
```
eAGLShareContext = ThreeEgl.getContext(key: 3);
```


# three_dart

Dart 3d라이브러리입니다. an easy to use, lightweight, cross-platform, general purpose 3D library. 

three.js rewrite by Dart. 3D for Flutter. Base on [flutter_gl](https://github.com/wasabia/flutter_gl)




support Web, iOS, Android, macOS, Windows

Linux TODO, need flutter_gl support

three.js r138


Example Demo on flutter web [https://wasabia.github.io/three_dart_example/#/](https://wasabia.github.io/three_dart_example/#/)


## Getting Started

First at all. Follow flutter_gl Usage [flutter_gl](https://github.com/wasabia/flutter_gl)


TODO


## Usage

check example project

```
camera = new three.PerspectiveCamera( 40, 1, 0.1, 10 );
camera.position.z = 3;

scene = new three.Scene();
camera.lookAt(scene.position);

scene.background = three.Color(1.0, 1.0, 1.0);
scene.add( new three.AmbientLight( 0x222244, null ) );

var geometryCylinder = new three.CylinderGeometry( 0.5, 0.5, 1, 32 );
var materialCylinder = new three.MeshPhongMaterial( { "color": 0xff0000 } );

mesh = new three.Mesh( geometryCylinder, materialCylinder );
scene.add( mesh );
```


## Example

```
cd example && flutter run
```


![3](https://user-images.githubusercontent.com/1768228/141482294-b78446b3-d9ab-4cc0-83fc-dbabaab459e2.png)


## TODO
- unit test
- more example
- README && Document
- and so on...

## Issues
File any issues, bugs, or feature requests.

## Contributing
Pull request please!

## Libraries and Plugins

[https://github.com/wasabia/three_dart_jsm](https://github.com/wasabia/three_dart_jsm)

[https://github.com/wasabia/opentype](https://github.com/wasabia/opentype)

[https://github.com/wasabia/typr_dart](https://github.com/wasabia/typr_dart)


# BabylonJs-Editor-Mesh-Test-GLB
A repo to capture the importation of a .glb file and my results from that

**Test 2: Solar System GLBFile**
-----
Expected:
![image|690x262](https://discourse-cloud-file-uploads.s3.dualstack.us-west-2.amazonaws.com/standard10/uploads/babylonjs/original/2X/3/3a60b060da6c7cc7abe68a7784e211d45a621c0d.jpeg) 

Importing
---
Dragging it right in basically works, the animation seems ot be working in the preview.
![solar-system|690x365](https://discourse-cloud-file-uploads.s3.dualstack.us-west-2.amazonaws.com/standard10/uploads/babylonjs/original/2X/3/36af89e719172eeb179cdf5d50b8c11f877e3ec6.gif) 

Here's what didn't work:
- the materials are mostly all black for some reason. This isn't the same as the broken-image thing. They are just black.
- animation does not run at all in the 'editor preview' after clicking `Play`
![image|690x380](https://discourse-cloud-file-uploads.s3.dualstack.us-west-2.amazonaws.com/standard10/uploads/babylonjs/original/2X/6/675e632ff991fd4d95ed3a9c0b281b8e62c5178d.png) 

**Reloading Editor Project**
--
This unfortunately doesn't work at all, here are the steps and logs:

1. I save the scene. I notice that none of the textures are output into the scene folder. I assume that should be right?
2. close the editor
3. Double click the just-saved project
4. **there is a critical failure**
![image|690x252](https://discourse-cloud-file-uploads.s3.dualstack.us-west-2.amazonaws.com/standard10/uploads/babylonjs/original/2X/8/836516b1f203961559adf8fc51d153ee3d91f510.png) 

Here is the log:
```
Uncaught (in promise) TypeError: Cannot set property 'invertY' of null
    at RawTexture../Materials/Textures/texture.ts.Texture.serialize (node_modules/babylonjs/babylon.max.js:66978)
    at eval (build/src/editor/scene/scene-manager.js:66)
    at Array.forEach (<anonymous>)
    at Function.SceneManager.SaveOriginalObjects (build/src/editor/scene/scene-manager.js:66)
    at Function.eval (build/src/editor/scene/scene-loader.js:220)
    at step (build/src/editor/scene/scene-loader.js:32)
    at Object.eval [as next] (build/src/editor/scene/scene-loader.js:13)
    at fulfilled (build/src/editor/scene/scene-loader.js:4)
```
Failure in `babylon.max.js
![image|690x144](https://discourse-cloud-file-uploads.s3.dualstack.us-west-2.amazonaws.com/standard10/uploads/babylonjs/original/2X/e/e4a52828b88e4144518bc5631830e28ecaee888e.png) 

**In a Web Project**
--
Since I cannot reload my saved project, I will attempt to make the web project in the same gesture as importation, so I will start over with a new scene and re-import.

this..kinda works.

1. open editor
2. `Project` > `New Project...`
3. Drag in the `solar_system.glb` file
4. Export Project Template
5. `yarn install && yarn build && yarn run webserver`

![image|690x309](https://discourse-cloud-file-uploads.s3.dualstack.us-west-2.amazonaws.com/standard10/uploads/babylonjs/original/2X/6/6f943a8febeac1956e592451a85804b6306615ea.png) 
- No textures
- No animations
- Interestingly no breaks otherwise, the camera works.



Here is the repo with all of the test results: 

https://github.com/simiancraft/BabylonJs-Editor-Mesh-Test-GLB

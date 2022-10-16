# a-water (ada-water)

Based on the shader tutorial by ada, this component produces a very cheap large ocean that reminds one of the style of Wind Waker.

This component give you a simple primitive that makes it easy to drop in and work with.

Full credit to [Ada Rose](https://twitter.com/adarosecannon). This component packages everything into one file in a very basic, crude way to make importing it and using it as simple as possible, but if you want to go through the course of building this yourself from first principles, check out their multi-part series on the topic: https://medium.com/samsung-internet-dev/generating-a-water-effect-part-1-svg-and-canvas-2ad07060cc0d

![image](https://user-images.githubusercontent.com/6391152/196059614-4b5144a4-882a-4105-86f1-1904d941fd3b.png)


```html
<!DOCTYPE html>
<html>
  <head>
    <script src="https://aframe.io/releases/1.3.0/aframe.min.js"></script>
    <script src="https://cdn.jsdelivr.net/gh/kylebakerio/ada-water/ada-water.js"></script>
  </head>
  <body>
    <a-scene>
<!--   magic is right here     -->
      <a-water></a-water>
      
      <a-camera wasd-controls="fly:true;"></a-camera>
      <a-box position="-1 0.5 -3" rotation="0 45 0" color="#4CC3D9"></a-box>
      <a-sphere position="0 1.25 -5" radius="1.25" color="#EF2D5E"></a-sphere>
      <a-cylinder position="1 0.75 -3" radius="0.5" height="1.5" color="#FFC65D"></a-cylinder>
      <a-sky color="#ECECEC"></a-sky>
    </a-scene>
  </body>
</html>
```


You can experiment with adding another layer of animation on it:
```js
document.querySelector('a-water').setAttribute('animation', {
    property: 'scale', 
    from: '10 2 1',
    to: '2 15 2',
    dur: 200000,
    loop: true,
    dir: 'alternate',
    easing: "easeOutElastic",
})
```


Added the primitive bindings you're most likely to want.

| Attribute    | Default              | Description |
| :---         |     :---:            |          :--- |
| width        | 10 (meters)    | git status    |
| length       | 10 (meters)       | git diff      |
| side     |  one of ["front", "back", "double"]       | whether to be visible from under the water as well      |
| base-color     | darkblue       | primary surface color      |
| foam-color     | white       | secondary surface color     |
| voronoi-points     | 15       | changes the shape of the 'foam'; try e.g. 50. Note: can only be set at init! baked into the shader.      |



You can also check ada-water.js for the up-to-date props in case I forget to update the readme when making a minor tweak.

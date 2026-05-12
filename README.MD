# Flatlist behind the scenes

## OnScroll
```javascript
onScroll={(event) => {
  console.log(event.nativeEvent);
}}
```

- Events
  - detect displacement
  - calculate visible items
  - virtualization
  - detect end of list
  

```javascript
{
   // internal spacing 
   "contentInset":{
      "bottom":0,
      "left":0,
      "right":0,
      "top":0
   },
   // How far the user has scrolled: x: horizontal, y: vertical
   // window.scrollY = 146
   // window.scrollX = 0
   "contentOffset":{
      "x":0,
      "y":146.66666666666666
   },
   // total content size
   "contentSize":{
      "height":5800,
      "width":390
   },
   // visible screen area
   "layoutMeasurement":{
      "height":794,
      "width":390
   },
   // target -> ID from native UI
   "target":926,
   "timestamp":176997375.6451667,
   "zoomScale":1
}
```

- Calculo
```javascript
distanceFromEnd = contentSize.height - layoutMeasurement.height - contentOffset.y
```

## onEndReached

```javascript
onEndReached={(info) => {
    console.log('onEndReached:', info);
}}
```

- If you want a customizable distance, you can use this property:
```javascript
threshold = layoutMeasurement.height * 0.5
onEndReachedThreshold={0.5}
```

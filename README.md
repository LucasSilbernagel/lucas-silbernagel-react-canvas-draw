<div align="center">
<h1>React Canvas Draw</h1>
</div>

Forked from [https://github.com/embiem/react-canvas-draw](https://github.com/embiem/react-canvas-draw)

## Installation

Install via NPM:

```
npm install lucas-silbernagel-react-canvas-draw
```

or YARN:

```
yarn add lucas-silbernagel-react-canvas-draw
```

## Usage

```javascript
import React from "react";
import ReactDOM from "react-dom";
import CanvasDraw from "lucas-silbernagel-react-canvas-draw";

ReactDOM.render(<CanvasDraw />, document.getElementById("root"));
```

For more examples, like saving and loading a drawing ==> look into the [`/demo/src` folder](https://github.com/LucasSilbernagel/lucas-silbernagel-react-canvas-draw/tree/master/demo/src).

### Props

These are the defaultProps of CanvasDraw. You can pass along any of these props to customize the CanvasDraw component. Examples of how to use the props are also shown in the [`/demo/src` folder](https://github.com/LucasSilbernagel/lucas-silbernagel-react-canvas-draw/tree/master/demo/src).

```javascript
  static defaultProps = {
    onChange: null
    loadTimeOffset: 5,
    lazyRadius: 30,
    brushRadius: 12,
    brushColor: "#444",
    catenaryColor: "#0a0302",
    gridColor: "rgba(150,150,150,0.17)",
    hideGrid: false,
    canvasWidth: 400,
    canvasHeight: 400,
    disabled: false,
    imgSrc: "",
    saveData: null,
    immediateLoading: false,
    hideInterface: false,
    gridSizeX: 25,
    gridSizeY: 25,
    gridLineWidth: 0.5,
    hideGridX: false,
    hideGridY: false
    enablePanAndZoom: false,
    mouseZoomFactor: 0.01,
    zoomExtents: { min: 0.33, max: 3 },
  };
```

### Functions

Useful functions that you can call, e.g. when having a reference to this component:

- `getSaveData()` returns the drawing's save-data as a stringified object
- `loadSaveData(saveData: String, immediate: Boolean)` loads a previously saved drawing using the saveData string, as well as an optional boolean flag to load it immediately, instead of live-drawing it.
- `getDataURL(fileType, useBgImage, backgroundColour)` will export the canvas to a data URL, which can subsequently be used to share or manipulate the image file.
- `clear()` clears the canvas completely, including previously erased lines, and resets the view. After a clear, `undo()` will have no effect.
- `eraseAll()` clears the drawn lines but retains their data; calling `undo()` can restore the erased lines. _Note: erased lines are not included in the save data._
- `resetView()` resets the canvas' view to defaults. Has no effect if the `enablePanAndZoom` property is `false`.
- `undo()` removes the latest change to the drawing. This includes everything drawn since the last MouseDown event.


## Tips

If you want to save large strings, like the stringified JSON of a drawing, I recommend you use [pieroxy/lz-string](https://github.com/pieroxy/lz-string) for compression. It's LZ compression will bring down your long strings to only ~10% of its original size.

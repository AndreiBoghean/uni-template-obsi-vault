/*
![](https://raw.githubusercontent.com/zsviczian/obsidian-excalidraw-plugin/master/images/scripts-grid.jpg)

The default grid size in Excalidraw is 20. Currently there is no way to change the grid size via the user interface. This script offers a way to bridge this gap.

See documentation for more details:
https://zsviczian.github.io/obsidian-excalidraw-plugin/ExcalidrawScriptsEngine.html

```javascript
*/
const api = ea.getExcalidrawAPI();
let appState = api.getAppState();
appState.gridSize = 40;

api.updateScene({
  appState,
  commitToHistory:false
});
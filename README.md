# CS4600 Fall 2021 — my coursework

Course: https://graphics.cs.utah.edu/courses/cs4600/fall2021/

Each `prjNN/` folder holds the official starter files. **Edit only `projectN.js`** (prj06 also needs GLSL code: it goes in the strings inside `project6.js`). The `.html` file is the course's UI and WebGL setup.

| Folder | Topic | You implement |
|---|---|---|
| prj01 | Compositing images | `composite` |
| prj02 | 2D transformations | `GetTransform`, `ApplyTransform` |
| prj03 | Curves (WebGL) | curve-drawing class |
| prj04 | Triangle meshes | `GetModelViewProjection`, `MeshDrawer` |
| prj05 | Shading | `MeshDrawer`, `GetModelViewMatrix`, Blinn fragment shader |
| prj06 | Ray tracing (GLSL) | `RayTracer`, `IntersectRay`, `Shade` |
| prj07 | Animation | `SimTimeStep` |

## Running (there is no compile step)

JavaScript runs straight in the browser, so there's nothing to compile. You just need a local web server. WebGL won't load images from `file://` pages.

**VS Code:** press **F5**, pick a project number. This starts the server and opens Chrome with the debugger attached.

**By hand:**
```
python -m http.server 8000
```
Then open http://localhost:8000/prj01/project1.html (change the numbers for other projects). Stop the server with Ctrl+C.

After you edit `projectN.js`:
- **F4** in the page reloads only your script and keeps the UI state (images you loaded and so on).
- **Ctrl+Shift+R** reloads the whole page with no cache. Use it if F4 seems stale.

## Debugging

- **Breakpoints in VS Code** (after F5): click left of a line number in `projectN.js`. When it's hit, hover over variables, step with F10/F11, and look at the Debug Console. If you reload with F4, the breakpoints may detach. Use Ctrl+R then.
- **Chrome DevTools** (F12): the Console tab shows errors with file:line. Sources tab → open `projectN.js` to set breakpoints there.
- `console.log(x)` prints to the Console. `debugger;` in your code pauses there while DevTools is open.
- **Shader errors** (prj03–06): the HTML prints GLSL compile errors with `alert`/console. Read the line number in the message.

## JS gotchas coming from C/C++/Python

- Declare with `let` (mutable) or `const`. Avoid `var` and undeclared variables.
- Numbers are all doubles. Use `Math.floor` for integer pixel indices.
- Image pixels (`ImageData.data`) are a flat `Uint8ClampedArray` of RGBA: index `(y*width + x)*4 + channel`.
- Matrices in WebGL code are flat 16-element arrays in **column-major** order.
- `==` coerces types. Use `===`.

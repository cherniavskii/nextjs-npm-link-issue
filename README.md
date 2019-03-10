This is reproduction example for https://github.com/zeit/next.js/issues/5463

Steps to reproduce:

1. Clone this repo locally.
2. In `package` folder:
  - `npm link`
3. In `web` folder:
  - `npm i`
  - `npm link package`
  - `npm run dev`
4. Go to [http://localhost:3000/](http://localhost:3000/) - package content is displayed correctly.
5. Modify `package/index.js` content, e.g.:
  ```diff
  - module.exports = 'package content';
  + module.exports = 'package content edited';
  ```
6. Reload page in browser


Observations:

Client bundle has updated `package` version, but server bundle has outdated one.
It results in page blinking and console warning, since server and client render different output.
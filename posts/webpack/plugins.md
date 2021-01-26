## HtmlWebpackPlugin

https://webpack.js.org/plugins/html-webpack-plugin/

번들링된 js 파일을 사용하는 html 파일을 생성해주는 플러그인이다.

html 파일을 `output.path` 경로에 생성되며,\
아무런 옵션없이 생성한 파일의 내용은 단순하다.

```html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8" />
    <title>Webpack App</title>
    <meta name="viewport" content="width=device-width,initial-scale=1" />
  </head>
  <body>
    <script src="app.js"></script>
  </body>
</html>
```

- title 변경
- favicon 추가
- body에 html 코드 추가

와 같은 내용의 추가 작업은 HtmlWebpackPlugin 플러그인의 옵션을 통해서 이루어진다.
각 옵션값으로도 가능하지만, 제일편한건 html파일을 만들어놓고 `template`으로 사용하는 것이다.

template option을 사용하면,\
template 으로 설정된 파일에 script 태그부분만 추가된다.

```shell
> npm i -D html-webpack-plugin
```

```js
const HtmlWebpackPlugin = require('html-webpack-plugin');

...
module.exports = {
    ...
    plugins: [
            new HtmlWebpackPlugin({
                template: path.join(`${template_file_path}`),
            })
        ],
    ...
}
```

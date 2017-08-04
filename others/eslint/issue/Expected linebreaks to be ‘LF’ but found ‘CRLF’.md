
# Expected linebreaks to be ‘LF’ but found ‘CRLF’

这就是eslint的报错了，可能是原作者用的是linux系统。
只需在eslintrc文件里面将

```javascript
/*eslint linebreak-style: ["error", "unix"]*/
```
修改为

```javascript
/*eslint linebreak-style: ["error", "windows"]*/
```
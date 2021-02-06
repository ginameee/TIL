npm 환경설정 파일이다.
사용하고있는 환경설정파일의 위치는 아래 커맨드를 통해 알 수 있다.

```shell
> npm config ls -l

...
unicode = true
update-notifier = true
usage = false
; user-agent = "npm/{npm-version} node/{node-version} {platform} {arch} {ci}" ; overridden by cli
userconfig = "/Users/we/.npmrc"  # <--- 환경설정 파일 위치
version = false
versions = false
viewer = "man"
...
```

만약 특정 경로의 환경설정파일을 사용하고 싶으면

```shell
> npm {command} --userconfig {npmrc_path}
```

사용하면 된다.

## 참고

- https://ohgyun.com/638

# 使用方式

为了最小程度的影响正常功能，所有新增的命令均有前缀 `+`。

命令格式为 `+命令名 参数1 参数2 ...`，可以写在任何一行，会被过滤或替换成特定的内容。

## 测试第一次失败

### 固定格式

格式：`+fd 你的名字???@战队名`。

用途：将 `???` 依次替换为 0、1、2……等进行对战，并在第一次失败后结束并输出对战内容。如果没有 `???` 则会在最后一个 `@` 之前追加一个。

注意：目前战队名是必须的。且在测试胜率时无效。

### 固定起点

格式：`+fd.start 起点`。

用途：固定 `???` 替换的起点。该命令仅在同时使用了 `+fd` 时生效。

### 例子

```plain
!test!
+fd ???+???@pbb
+fd.start 114

slime@!
```

将会按照：

- `slime@! 114+???@pbb` VS `115+???@pbb 116+???@pbb`
- `slime@! 117+???@pbb` VS `118+???@pbb 119+???@pbb`
- ……

的形式对战，并输出第一组 `slime@!` 所在队落败的对局。

```plain
!test!
+fd test@pbb
+fd.start 514

slime@!
slime@!
```

将会按照：

- `slime@!` VS `test514@pbb`
- `slime@!` VS `test515@pbb`
- ……

的形式对战，并输出第一组 `slime@!` 落败的对局。
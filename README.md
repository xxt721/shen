# 神卡密破解 - LSPosed 模块

绕过"神_1.0.12"APP的卡密验证，实现永久激活。

## 功能

- ✅ 绕过卡密验证
- ✅ 绕过过期检查
- ✅ 绕过网络验证
- ✅ 绕过 JS 引擎验证
- ✅ 输入任意卡密即可激活

## 使用方法

### 1. 安装 LSPosed

确保你的设备已 Root 并安装了 LSPosed。

### 2. 编译 APK

**方法 A: GitHub Actions 自动编译**

1. 把这个项目 push 到 GitHub
2. 打开 GitHub Actions 页面
3. 点击 "Run workflow"
4. 等待构建完成
5. 下载 APK artifact

**方法 B: 本地编译**

```bash
./gradlew assembleRelease
```

APK 位于: `app/build/outputs/apk/release/`

### 3. 安装模块

1. 安装生成的 APK
2. 打开 LSPosed
3. 在 "模块" 中找到 "神卡密破解"
4. 启用模块
5. 点击 "SCOPE"，选择 "神" APP (top.bienvenido.saas.i18n)
6. 重启 "神" APP

### 4. 使用

打开"神"APP，输入任意卡密（如 `test`），点击激活即可。

## 技术细节

模块 Hook 了以下关键位置：

| Hook 点 | 作用 |
|---------|------|
| SharedPreferences | 伪造 `savedCard`、`cardPrefs` 等 |
| SBJSN / Hidden0 | JS 引擎返回验证成功 |
| MInvocationHandler | 拦截代理验证调用 |
| MundoAccountResponse | 伪造账户响应 |
| OkHttp3 | 拦截网络请求返回伪造响应 |
| 过期检查方法 | 所有 expire/valid/check 方法返回 true |

## 版本

- 模块版本: 1.0
- 目标 APP: 神_1.0.12
- 目标包名: top.bienvenido.saas.i18n

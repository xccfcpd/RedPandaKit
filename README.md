# RedPandaKit

RedPanda-CPP 自定义编译工具链，用于 GitHub Actions 自动化编译。

## 两条编译线

| 编译线 | 编译器 | Qt | CMake / Ninja | 产物 |
| ------ | ------ | -- | ------------- | ---- |
| `build-qt5` | GCC 8.5（本仓库 `toolchain/` 分卷） | Qt 5.15.19 静态 | 工具链自带 | `*-win64.zip` |
| `build-qt6` | GCC 14.4.0 UCRT（mingw-lite r1.1） | Qt 6.8.5 静态 | runner 自带 | `*-win64-qt6.zip` |

Qt5 线保持原有行为不变；两条线默认都编译远端所有分支。Qt6 线可以用
`workflow_dispatch` 的 `qt6_branches` 输入缩小范围（留空 = 全部）。

## 包含内容（Qt5 工具链）

- GCC 8.5 (MinGW Lite, x86_64)
- Qt 5.15.19 (静态编译)
- CMake 3.31.12
- Ninja 1.13.2
- MinGW Make

## Qt6 工具链来源

- Qt: <https://github.com/xccfcpd/qt68lts-static/releases/tag/Qt_6.8.5-static-Release_mingw1440_64_UCRT>
- MinGW: <https://github.com/xccfcpd/mingw-lite/releases/tag/14.4-v1.1>

两个包在 workflow 里按固定 SHA256 校验，并缓存在 Actions Cache 中。

## 下载

见 [Releases](https://github.com/xccfcpd/RedPandaKit/releases)。

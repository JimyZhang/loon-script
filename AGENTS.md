# 仓库指南

## 项目结构

- `script/` 存放兼容 Loon 的 JavaScript 脚本，并按服务分目录组织。
- `qinglong/` 存放青龙专用脚本，优先使用 Node.js 和青龙环境变量运行，不承担 Loon 抓包入口职责。
- `loon/plugin/` 存放 Loon 插件定义，插件中的脚本地址指向 GitHub raw URL。
- `icons/` 存放插件元数据和订阅使用的 PNG 图标。
- `subscribe/` 存放生成后的订阅 JSON，例如图标订阅和 BoxJS 元数据。
- `.github/scripts/generate_image_json.py` 会根据 `icons/` 重新生成 `subscribe/leiyiyan.icons.json`。

## 开发说明

- 当前仓库没有包管理器清单，也没有本地构建系统。
- 大多数脚本都是独立自动化脚本，目标运行环境是 Loon 或兼容的脚本环境。
- 修改时尽量限定在目标服务目录，以及对应的插件或订阅元数据中。
- 除非任务需要更大范围清理，否则保留现有脚本环境辅助函数和命名风格。
- 不要把青龙 `client_id`、`client_secret`、token 或业务 Cookie 写死进仓库；这类敏感值必须通过运行时配置或环境变量读取。
- 不要提交 IDE 本地文件，例如 `.idea/`。

## 验证方式

- 当前没有定义自动化测试命令。
- 如果修改了图标订阅，在 `GITHUB_REPOSITORY` 和 `GITHUB_STATE` 可用时，从仓库根目录运行 `python .github/scripts/generate_image_json.py`；否则手动核对生成后的 JSON。
- 如果修改了 Loon 插件或脚本，检查语法，并确认引用的 GitHub raw URL 与仓库路径一致。

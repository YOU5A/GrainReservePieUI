# AGENTS.md — GrainReserve Pie UI

## 项目概述
- **项目名称**：GrainReserve Pie UI
- **类型**：Minecraft 基岩版（Bedrock Edition）UI 资源包（Resource Pack）
- **作者**：PFMAXLNX（pfmaxlnx@gmail.com，bilibili: PFMAXLNX）
- **版本**：1.1.0（format_version: 1）
- **兼容引擎**：min_engine_version [1, 1, 0]

## 目录结构说明
| 目录 / 文件 | 用途 |
|---|---|
| manifest.json | 资源包清单，定义包名、UUID、版本、子包 |
| pack_icon.png | 资源包图标 |
| locks.json | 方块定义 |
| iomes_client.json | 客户端生物群系配置 |
| splashes.json | 闪屏文本 |
| loading_messages.json | 加载消息 |
| nimations/ | 玩家动画定义（第一人称、披风、HUD 等） |
| nimation_controllers/ | 动画控制器 |
| entity/ | 实体定义（玩家 YOUSA、鱼钩等） |
| ogs/ | 各生物群系迷雾设置 |
| ont/ | 字体资源 |
| materials/ | 材质定义 |
| models/ | 模型文件 |
| particles/ | 粒子效果 |
| ender_controllers/ | 渲染控制器 |
| scripts/ | .ml 脚本文件（Core.ml、优化脚本等） |
| sounds/ | 音效资源 |
| subpacks/ | 子包（FPS 显示模块、资源包开关等） |
| 	exts/ | 文本 / 语言文件 |
| 	extures/ | 贴图资源（UI、实体、粒子等） |
| ui/ | UI 定义 JSON 文件 |

## UI 框架依赖
项目集成了多套第三方 UI 框架，修改时需注意各框架的命名空间和文件归属：

| 框架 | 路径 | 说明 |
|---|---|---|
| **RainbowPieUI** | ui/RainbowPieUI/ | 核心 UI 框架（screen、module、module_lib、common、ui_extras） |
| **MintUI** | ui/MintUI/、	extures/MintUI/ | 对话框、背景等 UI 组件 |
| **Minthawthorn** | ui/.Minthawthorn/ | HUD 和调试屏幕扩展 |
| **netease** | ui/netease/ | 网易版相关 UI（举报、语音、折叠菜单） |

## 子包系统
子包通过 manifest.json 中的 subpacks 数组定义，对应 subpacks/ 目录：
- **FPS Modules**：屏幕顶部 FPS 显示（含独立动画、模型、实体、贴图）
- **Resource Pack Closure**：关闭本资源包以加载其他资源包
- **Resource Pack Opening**：默认 UI 资源包（含 HUD、护甲等完整贴图资源）

## 编码规范

### JSON 文件
- 遵循 Minecraft Bedrock 资源包 JSON 格式规范
- UI JSON 中使用的命名空间前缀：
  - ainbowpie_ — RainbowPieUI 组件
  - mintui_ — MintUI 组件
  - mint_ — Minthawthorn 扩展
  - 
etease_ — 网易版组件
- 修改 UI JSON 时注意保持与 _ui_defs.json 和 _global_variables.json 中的变量/定义一致
- ui_defs 中引用的文件路径必须有效

### .ml 脚本
- 脚本文件位于 scripts/ 目录，使用 .ml 扩展名
- 核心入口：Core.ml
- 优化相关：OptimizarInicio.ml、OptimizarInicio2.ml、OptimizarAgua.ml、general_optimization.ml

### 贴图资源
- 格式：PNG（带透明通道）、部分 JPG
- .json 伴生文件用于定义贴图的九宫格拉伸（如 _white.json）
- lipbook_textures.json 和 	errain_texture.json 是贴图映射的关键文件

### 文件命名
- 使用 snake_case（下划线命名）
- UI 文件命名反映其功能屏幕（如 hud_screen.json、inventory_screen.json）
- 动画控制器使用 .controller.json 后缀

## 版权与安全约束
- **版权**：© PFMAXLNX 2019-2024，保留所有权利
- 不得将修改后的资源包发布到互联网
- 不得未经许可使用包内的 PNG/JSON 资源
- 不得将本资源包整合到其他作品一起发布
- **禁止批量删除**：禁止使用 m -rf、Remove-Item -Recurse、del /s 等批量删除命令
- 如需删除多个文件，停止操作并请求用户手动处理

## 通用规则
- 所有交互统一使用**中文**
- 使用 PowerShell 执行命令（不使用的命令：del /s、d /s、mdir /s、m -rf）
- 关联仓库：UserTool（https://github.com/YOU5A/UserTool）
- 修改 manifest.json 时注意保持 UUID 不变
- 新增 UI 文件后需在 ui/_ui_defs.json 中注册

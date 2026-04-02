---
description: Taro 小程序与 H5 开发的 AI 规则文件
globs: **/*.tsx, **/*.ts, **/*.less, **/*.json
alwaysApply: true
---

# 角色与目标

你是资深 Taro 前端开发工程师，负责微信小程序与 H5 的高质量交付。目标是产出可维护、性能稳定、视觉高度还原的代码，并严格遵循项目规范。

# 适用范围

- 适用于 Taro v3.6.x + React v18 项目
- 适用于页面开发、组件开发、样式实现、接口对接与状态管理
- 适用于蓝湖设计稿还原与“代码切图”重构

# 核心约束

## 必须

- 使用 TypeScript 与函数式组件
- 当涉及生成代码或生成页面时，优先使用文档集中 "taro-template" 模板进行代码生成；
- 页面位于 /src/pages，组件位于 /src/components 或页面同级 components
- 使用 .module.less + classnames 管理样式
- .less文件中的样式必需依据结构进行嵌套，避免平铺样式。嵌套层级不超过三层
- 页面内容主体必须显式指定 `box-sizing: border-box;`
- 必须严格使用rpx单位进行布局
- 接口调用统一使用 @wmeimob/request
- 优先使用 @wmeimob/taro-design 的业务组件；其次使用 @tarojs/components 的业务组件
- 无论什么页面都必须使用 PageContainer 和 MMNavigation 组件
- 当使用@wmeimob/taro-design 的业务组件时，必须阅读组件源码以保证可以正确使用
- 遵循既有代码风格与目录规范

## 禁止

- 使用 Class Component
- 在 TSX 中堆叠行内样式
- 绕过组件库直接用原生 HTML 标签
- 直接复制蓝湖生成代码而不进行重构

# 技术栈与依赖

- 核心框架: @tarojs/cli ^3.6.35 + React v18
- 状态管理: Zustand ^5.0.8
- 工程化: TypeScript ^4.1.0, Taro CLI, cross-env
- 样式方案: Less + CSS Modules + classnames
- 辅助工具: dayjs, number-precision

## Workspace 依赖

- @wmeimob/taro-design
- @wmeimob/taro-utils
- @wmeimob/react-hooks
- @wmeimob/request
- @wmeimob/utils
- @wmeimob/tencent-yun

# 工程规范

## 结构与命名

- 组件目录采用 kebab-case
- 默认入口使用 index.tsx 与 index.module.less
- 路由页面遵循 Taro 路由注册与目录规范

## 样式与布局

- 优先使用 Flex 布局
- 避免绝对定位堆叠
- 只在必须的动态样式场景使用行内样式

## 数据与交互

- 所有请求处理 loading 与 error 状态
- 全局状态使用 Zustand，局部状态使用 useState/useReducer
- 类型定义清晰，避免 any

# 蓝湖设计稿还原规范

## 视觉分析

- 拆解页面为 Header/Body/Footer 与核心交互模块
- 将视觉元素映射为业务组件与基础组件

## Taro 化重构

- div → View，span/p/h1 → Text，img → Image，button → Button
- 全局样式改为 .module.less
- 优化层级与定位，优先使用 Flex
- 将蓝湖远程图片替换为本地资源或项目内 CDN 常量

## 系统 UI 剔除规则

- 转换开始前先扫描并删除状态栏节点树
- 删除原生导航节点并用 MMNavigation 替代
- 删除底部安全区黑条节点，交由 PageContainer 处理

## HTML → TSX 标签转换

- div → View
- span → Text
- img → Image，必须添加 mode，且标签自闭合
- input → Input，遵循输入框专项规则
- button → Button
- class 转换为 className={styles.xxx} 且使用 camelCase

## 原子类聚合

- 从 common.css 读取原子类属性并合并到专属 LESS 类
- TSX 仅保留 styles.xxx，不允许保留原子类名

## CSS → LESS 样式转换

- 删除 overflow-wrap、word-break 等文字溢出属性
- 删除占位空节点与样式
- 删除页面级固定尺寸的宽高
- 固定宽度按撑满、内容自适应、固定宽优先级处理，保留则转为 rpx
- 父容器用 padding 控制左右间距，优先于子元素 margin

## Input 专项规则

- 输入框容器使用 display:flex 与 align-items:center
- 删除因设计稿造成的无意义占位 padding-right
- Input 本体使用 flex:1

## 图片引用规则

- 普通图片使用 Image 并通过 import 引入
- 背景图仅在 LESS 内引用，TSX 仅使用类名

## 自检清单

- 根节点使用 PageContainer
- 无任何占位省略代码
- 所有 import 均被实际使用
- 所有 styles.xxx 在 LESS 中有定义
- 背景图仅在 LESS 中引用
- 所有 Image 有 mode 且标签自闭合
- Input 容器与本体布局正确
- 无页面级固定尺寸
- 系统 UI 已剔除

## 语义组件替换

- 输入框使用组件库 Input
- 按钮使用组件库 Button
- 选择框使用组件库 Checkbox

## 逻辑注入

- 将静态文本抽为 props 或 state
- 补齐必要交互与事件处理
- 保证组件可复用与可扩展

# 交付物与质量要求

- 输出完整 TSX 页面与对应 .module.less
- 代码可运行、可复用、无冗余结构
- 若项目提供 lint/typecheck/test 脚本，必须执行并修复问题

# 沟通与协作

- 使用中文沟通，表达简洁清晰
- 信息不完整时先做合理假设并说明

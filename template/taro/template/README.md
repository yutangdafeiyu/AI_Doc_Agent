# 模板参考：结构与选择标准

## 模板选择决策树

```
源码包含无限滚动列表 / 下拉刷新 / 上拉加载语义？
├─ 是 → taro-list-page
└─ 否
    ├─ 是独立全屏页面（有导航、独立路由）？
    │   └─ 是 → taro-function-page
    └─ 是从页面剥离的局部 UI（弹窗/表单块/卡片/列表项）？
        └─ 是 → taro-function-component
```

---

## 模板一：[taro-function-page](./taro-function-page.md)

**适用**：普通独立全屏页面（含头部导航、主体内容）。

## 模板二：[taro-list-page](./taro-list-page.md)

**适用**：含下拉刷新、上拉加载、无限滚动的列表页。

---

## 模板三：[taro-function-component](./taro-function-component.md)

**适用**：所有非页面的独立 UI 组件（弹窗、表单块、独立卡片、列表项等）。

> **注意**：function-component 不使用 `PageContainer`，不使用 `MMNavigation`。

** 当选择模版以后，需要显式告知用户所使用的模版 **

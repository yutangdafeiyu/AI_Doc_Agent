---
name: '@wmeimob/taro-list-page'
type:
  - taro-page
description: 列表页模板
tags: []
---

# 模板说明
列表页模板

## 文件内容

### index.tsx
```tsx
import Taro from '@tarojs/taro'
import { FC, memo, useEffect } from 'react'
import { View } from '@tarojs/components'
import styles from './index.module.less'
import MMNavigation from '@wmeimob/taro-design/src/components/navigation'
import PageContainer, { useToast } from '@wmeimob/taro-design/src/layout/pageContainer'
import MMPullToRefresh, { useMMPullToRefresh } from '@wmeimob/taro-design/src/components/pull-to-refresh'
import MMEmpty from '@wmeimob/taro-design/src/components/empty'

// export interface IPageParams {}

interface I[:=PascalName:]Props {}

const Component: FC<I[:=PascalName:]Props> = () => {
  // const toast = useToast()
  // const { } = useRouterParams<IPageParams>({
  //   defaultParams: { }
  // })

  const [info, props] = useMMPullToRefresh({
    initRequest: true,
    getData(data) {
      return Promise.resolve({
        data: {
          list: [{ id: 1, name: 'test' }],
          isLastPage: true,
          total: 0
        }
      })
    }
  })

  return (
    <PageContainer className={styles.[:=CamelCaseName:]Style}>
      <MMNavigation title="[:=CamelCaseName:]" />

      <MMPullToRefresh {...props} empty={info.isEmpty && <MMEmpty />}>
        {info.list.map((item) => (
          <View key={item.id}>{item.name}</View>
        ))}
      </MMPullToRefresh>
    </PageContainer>
  )
}

const [:=PascalName:] = memo(Component)
export default [:=PascalName:]
```

### index.module.less
```less
.[:=CamelCaseName:]Style {
  height: 100%;
}
```

### index.config.ts
```tsx
export default definePageConfig({
  disableScroll: true
})
```

---
name: '@wmeimob/taro-function-page'
type:
  - taro-page
description: 页面模板
tags: []
---

# 模板说明
页面模板

## 文件内容

### index.tsx
```tsx
import Taro from '@tarojs/taro'
import { FC, memo, useEffect } from 'react'
import { View } from '@tarojs/components'
import styles from './index.module.less'
import MMNavigation from '@wmeimob/taro-design/src/components/navigation'
import PageContainer, { useToast } from '@wmeimob/taro-design/src/layout/pageContainer'

// export interface IPageParams {}

interface I[:=PascalName:]Props {}

const Component: FC<I[:=PascalName:]Props> = () => {
  // const toast = useToast()
  // const { } = useRouterParams<IPageParams>({
  //   defaultParams: { }
  // })

  useEffect(() => {}, [])

  return (
    <PageContainer className={styles.[:=CamelCaseName:]Style}>
      <MMNavigation title="[:=CamelCaseName:]" />

      <View>[:=CamelCaseName:]</View>
    </PageContainer>
  )
}

const [:=PascalName:] = memo(Component)
export default [:=PascalName:]
```

### index.module.less
```less
.[:=CamelCaseName:]Style { }
```

### index.config.ts
```tsx
export default definePageConfig({
  disableScroll: true
})
```

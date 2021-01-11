# tabs
uni-app Tab组件，支持角标显示


## 组件使用方式

将 **long-categories** 复制到 uni-app项目中的 **components**目录即可

```vue
<template>
	<view>
		<long-tabs 
			:list="list"
			v-model="active"
			activeTextColor=""
		>
		</long-tabs>
		<view style="padding: 20px" v-for="(item, index) in list" :key="index" v-if="active === index">
			{{ item.label }}
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				list: [],
				active: 0
			}
		},
		onLoad() {
			this.init()
		},
		watch: {
			active (val) {
				
			}
		},
		methods: {
			init () {
				this.list = [
					{ label: '全部'},
					{ label: '待清洁', badge: { bgcolor: '#F53B26', value: 12 } },
					{ label: '已清洁', badge: { bgcolor: '#6F61DA', value: 12 } },
					{ label: '已完成', badge: { bgcolor: '#2FC456', value: 12 } }
				]
			}
		}
	}
</script>

```

## 属性

| 名称            | 类型   | 默认值  | 说明                              |
| --------------- | ------ | ------- | --------------------------------- |
| list            | Array  | []      | tabs数据                          |
| v-model         | Number | 0       | 当前选中Tab索引                   |
| activeColor     | String | #F88F1A | 激活tab底部边框颜色，             |
| activeTextColor | String | 空      | 激活tab文字颜色，使用组件默认颜色 |


## list数据结构

| 名称  | 类型   | 说明                                         |
| ----- | ------ | -------------------------------------------- |
| label | String | 显示文字                                     |
| badge | Object | 角标对象，如果不需要角标显示。不写该属性即可 |

### badge数据结构

| 名称    | 类型   | 说明                          |
| ------- | ------ | ----------------------------- |
| bgcolor | String | 角标背景颜色，默认为：#F53B26 |
| value   | String | 角标的显示值                  |


## 使用示例

Github：https://github.com/songhailong8174/tabs

详细代码 [Demo](https://github.com/songhailong8174/tabs)

## 插件截图

![img](https://cdn.jsdelivr.net/gh/songhailong8174/images/img/long-tabs.png)


PS：如有问题可联系QQ（1365763165）或者提issure，如果帮到你了还请不要吝啬给个 [Star](https://github.com/songhailong8174/tabs)


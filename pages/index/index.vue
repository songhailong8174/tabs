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

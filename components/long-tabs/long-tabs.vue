<template>
	<view class="long-tabs">
		<view class="tabs-item" 
			v-for="(item, index) in list" 
			:key="index"
			:class="{ 'active': index === active }"
			@click="tabClick(index)"
		>
			<view class="item-label" 
				:style="{ 
					'border-color': activeColor, 
					'color': (index == active && activeTextColor != '') ? activeTextColor : ''
				}"
			>
				<view>{{ item.label }}</view>
				<view 
					class="badge" 
					v-if="item.badge && item.badge.value"
					:style="{ 'background-color':  item.badge.bgcolor != '' ? item.badge.bgcolor : badgeBgColor }"
				>
					{{ item.badge.value }}
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		model: {
			prop: 'value',
			event: 'change'
		},
		props: {
			list: {
				type: Array,
				default: () => []
			},
			value: {
				type: Number,
				default: 0
			},
			activeColor: {
				type: String,
				default: '#F88F1A'
			},
			activeTextColor: {
				type: String,
				default: ''
			}
		},
		data() {
			return {
				active: 0,
				badgeBgColor: '#F53B26'
			};
		},
		watch: {
			value: {
				immediate: true,
				handler (val) {
					this.active = val
				}
			},
			active: {
				immediate: true,
				handler () {
					this.$emit('change', this.active)
				}
			}
		},
		methods: {
			tabClick (index) {
				this.active = index
			}
		}
	}
</script>

<style lang="scss" scoped>
	.long-tabs {
		display: flex;
		justify-content: space-between;
		margin: 0 40upx;
		user-select: none;
		background-color: #fff;
		border-bottom: 2upx solid #E1E1E1;
		color: #1C1C1C;
		line-height: 100upx;
		font-weight: 400;
		.tabs-item {
			cursor: pointer;
			font-size: 28upx;
			position: relative;
			color: #000;
			text-align: left;
			box-sizing: border-box;
			background-color: #fff;
			.item-label {
				display: flex;
				justify-content: space-between;
				justify-items: center;
				position: relative;
				padding: 0 20upx;
				.badge {
					display: inline-block;
					margin: 30upx 0 0 20upx;
					width: 28upx;
					height: 28upx;
					padding: 6upx;
					line-height: 28upx;
					border-radius: 50%;
					background: #F53B26;
					color: #FFFFFF;
					font-size: 16upx;
				}
			}
		}
		.active {
			.item-label {
				border-bottom: 4upx solid transparent;
			}
		}
	}
</style>

<template>
	<view class="content">
		<jContacts ref="jContacts" :mode="mode" :hashFirst="hashFirst" @confirm="contactsConfirm" @cancel="contactsCancel"></jContacts>
		
		<view class="uni-padding-wrap uni-common-mt">
			<view class="uni-btn-v">
				<button type="default" @tap="show('single')">单选模式</button>
				<button type="default" @tap="show('multi')">多选模式</button>
				<button type="default" @tap="chooseList = []">清除</button>
			</view>
		</view>
		<view class="" v-for="(value, index) in chooseList" :key="index">
			{{value.name}}&nbsp;&nbsp;{{value.phone}}
		</view>
		
	</view>
</template>

<script>
	import jContacts from "@/components/j-contacts/j-contacts.vue"
	
	export default {
		components: {
			jContacts,
		},
		data() {
			return {
				showMask: false,
				mode: "single",
				hashFirst: false,
				chooseList: [],
			}
		},
		methods: {
			
			show(mode) {
				this.showMask = true
				this.mode = mode
				this.$refs.jContacts.show()
			},
			contactsConfirm(res) {
				this.chooseList = res
				console.log("返回结果：", JSON.stringify(this.chooseList))
			},
			contactsCancel(){
				
			},

		},
	}
</script>

<style>
	.content {
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
	}

	.logo {
		height: 200rpx;
		width: 200rpx;
		margin-top: 200rpx;
		margin-left: auto;
		margin-right: auto;
		margin-bottom: 50rpx;
	}

	.text-area {
		display: flex;
		justify-content: center;
	}

	.title {
		font-size: 36rpx;
		color: #8f8f94;
	}
</style>

<template>
	<div>
		<div class="content-wrapper">
			<div class="avatar">
				<img :src="seller.avatar">
			</div>
			<div class="title">
				<div class="name">
					<span class="brand"></span>
					<span class="content">
						{{seller.name}}
					</span>
				</div>
				<div class="description">{{seller.description}}/{{seller.deliveryTime}}分钟送达</div>
				<div class="support" v-if='seller.supports'>
					<span class="type" :class='[supportBadge]'>
					</span>
					<span class="content">{{seller.supports[0].description}}</span>
				</div>
				<div class="supportCount" v-if='seller.supports'>
					<span class="count">{{seller.supports.length}}个</span>
					<i></i>
				</div>
			</div>
		</div>
		<div class="bulletin-wrapper">
			
		</div>
	</div>
</template>
<script type="text/javascript">
	export default {
		name: 'myHeader',
		data() {
			return {
			}
		},
		props: [
			'seller'
		],
		computed: {
			supportBadge: function(){
				var supportBadge = '';
				//this.seller是异步加载来的数据，初始值是{}，需要加判断，dom中同理
				if(this.seller.supports){
					switch(this.seller.supports[0].type) {
						case 0: supportBadge = 'decrease';break;
						case 1: supportBadge = 'discount';break;
						case 2: supportBadge = 'special';break;
						case 3: supportBadge = 'invoice';break;
						case 4: supportBadge = 'guarantee';break;
					}
				}
				return supportBadge;
			}
		}
		
	}
</script>
<style type="text/css" lang="scss" scoped>
	@import "../../common/style/mixin.scss";
	.content-wrapper {
		background-color: #000;
		padding: 24px 12px 18px 24px;
		color: #FFF;
		font-size: 0;
		position: relative;
		.avatar {
			display: inline-block;
			vertical-align: top;
			img {
				width: 64px;
				height: 64px;
				border-radius: 4px;
			}
		}
		.title {
			display: inline-block;
			vertical-align: top;
			padding-top: 2px;
			padding-left: 16px;
			.name {
				.brand {
					display: inline-block;
					vertical-align: top;
					width: 30px;
					height: 18px;
					@include bg-img('./img/brand');
				}
				.content {
					font-size: 16px;
					font-weight: bold;
					line-height: 18px;
					margin-left: 6px;
				}
			}
			.description {
				font-size: 12px;
				font-weight: 200;
				line-height: 12px;
				margin-top: 8px;
				margin-bottom: 10px;
			}
			.support {
				margin-bottom: 2px;
				font-size: 0;
				.type {
					display: inline-block;
					vertical-align: top;
					width: 12px;
					height: 12px;
					&.decrease {
						@include bg-img('./img/decrease_1');
					}
					&.discount {
						@include bg-img('./img/discount_1');
					}
					&.special {
						@include bg-img('./img/special_1');
					}
					&.invoice {
						@include bg-img('./img/invoice_1');
					}
					&.guarantee {
						@include bg-img('./img/guarantee_1');
					}
				}
				.content {
					font-size: 10px;
					margin-left: 4px;
				}
			}
			.supportCount {
				position: absolute;
				right: 0;
				top: 100%;
				width: 48px;
				height: 24px;
				background-color: rgba(0,0,0,0.2);
			}
		}

	}
</style>
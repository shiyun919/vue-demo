
<template>
	<div>
		<!-- {{n}} -->
		<div class="wrapper" v-on:click="clickSelf">
			<template v-if="a">{{text}}</template>
			<template v-else></template>
		</div>
	</div>
</template>

<script>
	export default {
		props:["n"],
		data: () => {
			return {a: false, text: ""};
		},
		methods: {
			clickSelf(){
				if(this.text !== ""){
					return;   //如果text值不为空，就不能点击了，直接输出
				}
				this.a = true;
				this.text = this.n % 2 === 0 ? "x" : "o";
				this.$emit('click', this.text);  //通知App.vue Cell所在的div被点击了，与v-on:click一起使用
			}
		}
	}
</script>

<style>
	.wrapper {
		border: 1px solid #000;
		width: 100px;
		height: 100px;
		display: flex;
		justify-content: center;
		align-items: center;
		font-size: 32px;
		margin: -1px 0px 0px -1px;
	}
</style>

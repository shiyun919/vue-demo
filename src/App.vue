<template>
	<div class="container">
		<div class="title">棋盘</div>
			<!-- <div class="nuit">n的值为{{n}}</div> -->
			<div class="row">
				<Cell v-on:click="clickCell(0, $event)" v-bind:n="n" />
				<Cell v-on:click="clickCell(1, $event)" v-bind:n="n" />
				<Cell v-on:click="clickCell(2, $event)" v-bind:n="n" />
				<Cell v-on:click="clickCell(3, $event)" v-bind:n="n" />
				
			</div>
			<div class="row">
				<Cell v-on:click="clickCell(4, $event)" v-bind:n="n" />
				<Cell v-on:click="clickCell(5, $event)" v-bind:n="n" />
				<Cell v-on:click="clickCell(6, $event)" v-bind:n="n" />
				<Cell v-on:click="clickCell(7, $event)" v-bind:n="n" />
				
			</div>
			<div class="row">
				<Cell v-on:click="clickCell(8, $event)" v-bind:n="n" />
				<Cell v-on:click="clickCell(9, $event)" v-bind:n="n" />
				<Cell v-on:click="clickCell(10, $event)" v-bind:n="n" />
				<Cell v-on:click="clickCell(11, $event)" v-bind:n="n" />
				
			</div>
			<div class="row">
				<Cell v-on:click="clickCell(12, $event)" v-bind:n="n" />
				<Cell v-on:click="clickCell(13, $event)" v-bind:n="n" />
				<Cell v-on:click="clickCell(14, $event)" v-bind:n="n" />
				<Cell v-on:click="clickCell(15, $event)" v-bind:n="n" />
			</div>
			<!-- <div>{{map}}</div> -->
			<div class="result">胜方为：<span>{{result}}</span></div>
	</div>
</template>

<script>
	import Cell from "./Cell.vue";
	export default {
		components: {
			Cell
		},
		data() {
			return {
				n: 0,
				map: [[null,null,null,null],	[null,null,null,null],	[null,null,null,null],	[null,null,null,null]],
				result: false
			};
		},
		methods: {
			clickCell(b,text) {
				console.log('这个Cell被点击了')
				console.log(`第${b}号被点击, 内容是:${text}`) //0 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15
				this.map[Math.floor(b/4)][b%4] = text 
				this.n += 1   //n的值 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16
				this.tell()
			},
			tell(){     //tell就是判断，判断结果
				const map = this.map
				for(let i=0; i<3; i++){
					if(map[i][0] !== null && map[i][0] === map[i][1] && map[i][1] === map[i][2] && map[i][2] === map[i][3]){
						this.result = map[i][0]
					}
				}
				for(let j=0; j<3; j++){
					if(map[0][j] !== null && map[0][j] === map[1][j] && map[1][j] === map[2][j] && map[2][j] === map[3][j]){
						this.result = map[0][j]
					}
				}
				if(map[0][0] !== null && map[0][0] === map[1][1] && map[1][1] === map[2][2] && map[2][2] === map[3][3]){
					this.result = map[0][0]
				}
				if(map[0][3] !== null && map[0][3] === map[1][2] && map[1][2] === map[2][1] && map[2][1] === map[3][0]){
					this.result = map[0][3]
				}
			}
		},
	};
</script>

<style>
	* {
		margin: 0;
		padding: 0;
		box-sizing: border-box;
	}
	.container {
		max-width: 408px;
		margin: 0 auto;
		
	}
	.title {
		font-size: 18px;
		text-align: center;
		margin: 20px 0;
	}
	
	.nuit {
		text-align: center;
		margin: 20px 0;
	}

	.row {
		display: flex;
	}
	.result {
		font-size: 20px;
		margin: 20px 0px;
	}
	.result span {
		font-weight: bold;
		color: #FF0000;
	}
</style>



<!-- b 
0 map[0][0]    b为0时，就是map的第0行的第0个
1 map[0][1]    b为1时，就是map的第0行的第1个
2 map[0][2]    b为2时，就是map的第0行的第2个
3 map[0][3]    b为3时，就是map的第0行的第3个
4 map[1][0]    b为4时，就是map的第1行的第0个
5 map[1][1]    b为5时，就是map的第1行的第1个
6 map[1][2]    b为6时，就是map的第1行的第2个
7 map[1][3]    b为7时，就是map的第1行的第3个
8 map[2][0]    b为8时，就是map的第2行的第0个
9 map[2][1]    b为9时，就是map的第2行的第1个
10 map[2][2]    b为10时，就是map的第2行的第2个
11 map[2][3]    b为11时，就是map的第2行的第3个
12 map[3][0]    b为12时，就是map的第3行的第0个
13 map[3][1]    b为13时，就是map的第3行的第1个
14 map[3][2]    b为14时，就是map的第3行的第2个
15 map[3][3]    b为15时，就是map的第3行的第3个

map[Math.floor(b/4)][b%4] -->
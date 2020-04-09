<template>
	<view>
		
		<block v-for="(item,index) in list" :key="index">
			<paper-list :item="item"></paper-list>
		</block>
		
	</view>
</template>

<script>
	import paperList from "../../components/paper/paper-list.vue";
	
	export default {
		components: {
			paperList,
		},
		data() {
			return {
				list:[
						{
							userpic:"../../static/demo/userpic/1.jpg",
							username:"昵称",
							time:"10:21",
							data:"我是信息",
							noreadnum:2
						},
						{
							userpic:"../../static/demo/userpic/2.jpg",
							username:"昵称",
							time:"10:21",
							data:"我是信息",
							noreadnum:0
						},
						{
							userpic:"../../static/demo/userpic/3.jpg",
							username:"昵称",
							time:"10:21",
							data:"我是信息",
							noreadnum:0
						},
						{
							userpic:"../../static/demo/userpic/4.jpg",
							username:"昵称",
							time:"10:21",
							data:"我是信息",
							noreadnum:11
						},
						{
							userpic:"../../static/demo/userpic/5.jpg",
							username:"昵称",
							time:"10:21",
							data:"我是信息",
							noreadnum:2
						},
						{
							userpic:"../../static/demo/userpic/6.jpg",
							username:"昵称",
							time:"10:21",
							data:"我是信息",
							noreadnum:0
						},
						{
							userpic:"../../static/demo/userpic/7.jpg",
							username:"昵称",
							time:"10:21",
							data:"我是信息",
							noreadnum:0
						},
						{
							userpic:"../../static/demo/userpic/8.jpg",
							username:"昵称",
							time:"10:21",
							data:"我是信息",
							noreadnum:11
						}
					]
				}
		},
		methods: {
			
		}
	}
</script>

<style>

</style>

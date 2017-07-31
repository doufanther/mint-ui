<template>
  	<div class="shufa">
  			<!--<ul
			  v-infinite-scroll="loadMore"
			  infinite-scroll-disabled="loading"
			  infinite-scroll-distance="10">
			  	<li v-for="item in list">{{ item }}</li>
			</ul>-->
			<p @click="toast">toast</p>
			<p @click="MessageBox">MessageBox</p>
			<p @click="aa">22</p>
			<mt-popup
			  v-model="popupVisible"
			  position="top"
			>
				<h1>兜兜</h1>
			</mt-popup>
			<mt-swipe :auto="4000" class="aa" @change="handleChange">
				<mt-swipe-item class="sp">
					<div>111111111</div>
				</mt-swipe-item>
				<mt-swipe-item class="sp">
					<div>22222222222222</div>
				</mt-swipe-item>
				<mt-swipe-item class="sp">
					<div>33333333333333</div>
				</mt-swipe-item>
			</mt-swipe>
  	</div>
</template>

<script>
	import { Toast,MessageBox, Popup, Swipe, SwipeItem } from 'mint-ui';
	
  export default {
    data() {
      return {
        list:[1,2,3,4,5,6,7,8,9,10,11,12,13,14,15,16,17,18,19,20],
        popupVisible:false
      }
    },
    components:{
    	'mt-swipe':Swipe,
    	'mt-swipe-item':SwipeItem
    },
    methods:{
    	loadMore() {
		  this.loading = true;
		  setTimeout(() => {
		    let last = this.list[this.list.length - 1];
		    for (let i = 1; i <= 10; i++) {
		      this.list.push(last + i);
		    }
		    this.loading = false;
		  }, 2500);
		},
		toast(){
			Toast({
			  message: '操作成功',
			  iconClass: 'icon icon-success'
			});
		},
		MessageBox(){
			MessageBox.prompt({message:'nihao', title:'888'});
		},
		aa(){
			this.popupVisible=true;
		},
		handleChange(index){
			console.log(index);
		}
    }
  }
</script>
<style scoped>
	.aa,.sp{height: 100px;}
</style>
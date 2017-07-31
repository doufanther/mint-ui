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
			<mt-range v-model="rangeValue"></mt-range>
			<mt-progress :value="20" :bar-height="5"></mt-progress>
			<button @click="uploading">上传文件</button>
			<mt-progress :value="val" v-show="val">
				<div slot="start"></div>
				<div slot="end">{{val}}</div>
			</mt-progress>
			<mt-picker :slots="slots" @change="onValuesChange"></mt-picker>
  	</div>
</template>

<script>
	import { Toast,MessageBox, Popup, Swipe, SwipeItem } from 'mint-ui';
	
  export default {
    data() {
      return {
        list:[1,2,3,4,5,6,7,8,9,10,11,12,13,14,15,16,17,18,19,20],
        popupVisible:false,
        rangeValue:30,
        val:0,
        slots: [
        {
          flex: 1,
          values: ['2015-01', '2015-02', '2015-03', '2015-04', '2015-05', '2015-06'],
          className: 'slot1',
          textAlign: 'right'
        }, {
          divider: true,
          content: '-',
          className: 'slot2'
        }, {
          flex: 1,
          values: ['2015-01', '2015-02', '2015-03', '2015-04', '2015-05', '2015-06'],
          className: 'slot3',
          textAlign: 'left'
        }
      ]
      }
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
			//console.log(index);
		},
		uploading(){
			let aa=setInterval(()=>{
				this.val++;
				if(this.val===101){
					clearInterval(aa);
					this.val=0;
					Toast({
					  message: '操作成功',
					  iconClass: 'icon icon-success'
					});
				}
			},30)
		},
		onValuesChange(picker, values) {
	      if (values[0] > values[1]) {
	        picker.setSlotValue(1, values[0]);
	        console.log(picker)
	      }
	    }
    }
  }
</script>
<style scoped>
	.aa,.sp{height: 100px;}
</style>
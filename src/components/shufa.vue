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
			<p>{{selected}}</p>
			<!--<mt-tabbar v-model="selected">
				  <mt-tab-item id="外卖">
				    <img slot="icon" src="../assets/logo.png">
				    外卖
				  </mt-tab-item>
				  <mt-tab-item id="订单">
				    <img slot="icon" src="../assets/logo.png">
				    订单
				  </mt-tab-item>
				  <mt-tab-item id="发现">
				    <img slot="icon" src="../assets/logo.png">
				    发现
				  </mt-tab-item>
				  <mt-tab-item id="我的">
				    <img slot="icon" src="../assets/logo.png">
				    我的
				  </mt-tab-item>
			</mt-tabbar>-->
			<!--<mt-navbar v-model="selected">
				  <mt-tab-item id="1">选项一</mt-tab-item>
				  <mt-tab-item id="2">选项二</mt-tab-item>
				  <mt-tab-item id="3">选项三</mt-tab-item>
			</mt-navbar>
			
			tab-container 
			<mt-tab-container v-model="selected">
				  <mt-tab-container-item id="1">
				    <mt-cell v-for="n in 10" :title="'内容 ' + n" />
				  </mt-tab-container-item>
				  <mt-tab-container-item id="2">
				    <mt-cell v-for="n in 4" :title="'测试 ' + n" />
				  </mt-tab-container-item>
				  <mt-tab-container-item id="3">
				    <mt-cell v-for="n in 6" :title="'选项 ' + n" />
				  </mt-tab-container-item>
			</mt-tab-container>-->
			<mt-button size="small">small</mt-button>
			<mt-button size="large">large</mt-button>
			<mt-button size="normal">normal</mt-button>
			<mt-button plain>plain</mt-button>
			<mt-button icon="back">back</mt-button>
			<mt-button icon="more">更多</mt-button>
			<div ref="dec">
				<mt-cell-swipe
				  title="标题文字"
				  :right="[
				    {
				      content: '删除',
				      style: { background: 'red', color: '#fff' },
				      handler: () =>{this.$messagebox.confirm('确定执行此操作?').then(action => {
	 									bb();		
									});
								}
				    }
				  ]" >
				  </mt-cell-swipe>
			</div>
			<!--<mt-search
			  v-model="value"
			  cancel-text="取消"
			  placeholder="搜索">
			</mt-search>-->
			<mt-switch v-model="value8">开关</mt-switch>
			<mt-checklist
			  title="复选框列表"
			  v-model="value"
			  :options="options">
			</mt-checklist>
			<div>{{value}}</div>
			<mt-field label="生日" placeholder="请输入生日" type="date" v-model="birthday"></mt-field>
			<div>{{birthday}}</div>
			<div>
				<mt-badge type="primary">30</mt-badge>
				<mt-badge type="error">10</mt-badge>
				<mt-badge type="success">10</mt-badge>
				<mt-badge type="warning">10</mt-badge>
			</div>
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
      	selected:'',
      	value8:false,
      	value:[],
      	options:'',
      	birthday:''
      }
    },
   	created(){
   		this.options = [
		  {
		    label: '被禁用',
		    value: '值F',
		    disabled: true
		  },
		  {
		    label: '选中禁用',
		    value: '选中禁用的值',
		    disabled: true
		  },
		  {
		    label: '选项A',
		    value: '值A'
		  },
		  {
		    label: '选项B',
		    value: '值B'
		  }
		];
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
		bb(){
			this.$refs.dec.remove();
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
			},15)
		},
		
    }
  }
</script>
<style scoped>
	.aa,.sp{height: 100px;}
</style>
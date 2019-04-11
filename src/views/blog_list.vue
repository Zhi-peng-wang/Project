<template>
	<div>
		<h3>ajax基础：</h3><br>
		<ul>
			<li v-for="(t,index) in blogid_title" :key="index">
				 <a href="" class="list-group-item">{{t.title}}</a>
				<!--<router-link :to="`/${$route.params.id}/blog/blog_content/${t.blogid}`" class="list-group-item">-->
					<!--{{t.title}}-->
				<!--</router-link>-->
			</li>
		</ul>
	</div>
</template>

<script>
import event from '@/event.js'
export default{
	data(){
		return{
      blogid_title:[]
		}
	},
	create(){

  },
  mounted(){
    event.$on('toChangeTitle',  msg => {
      console.log("第一个组件信息：");
      console.log(msg);
      this.blogid_title=msg;
    })
  }
}
</script>

<style>
</style>

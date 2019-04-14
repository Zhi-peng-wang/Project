<template>
	<div>
		<h3>ajax基础：</h3><br>
		<ul>
			<li v-for="(t,index) in blogid_title" :key="index">
				 <!--<a @click.native="send_blogid(t.blogid)" class="list-group-item">{{t.title}}</a>-->
        <!--4.11晚写的留明早测试-->
        <router-link :to="`/${$route.params.id}`+'/blog/blog_content'"
                     class="list-group-item"
                     @click.native="send_blogid(t.blogid)">{{t.title}}</router-link>
			</li>
		</ul>
	</div>
</template>

<script>
import event from '@/event.js'
import {getBlog} from "../api";
export default{
	data(){
		return{
      blogid_title:[]
		}
	},
  mounted(){
    event.$on('toChangeTitle',  msg => {
      // console.log("第一个组件信息：");
      // console.log(msg);
      this.blogid_title=msg;
      console.log("blog_list组件");
      console.log(this.blogid_title);
    })
  },
  methods:{
	  send_blogid(blogid){
      console.log("发送blogid事件被触发,传递bolgid值为:"+blogid);
      getBlog({blogid:blogid})
        .then(res=>{
          console.log("blog_list组件请求日志的详情内容成功");
          console.log(res);
          //兄弟组件传值  传递日志的详情内容
          event.$emit('toChangeBlog',res);
        }).catch(error=>{
          console.log(error)
      })
    }
  }
}
</script>

<style>
</style>

<template>
  <div >
	  <!--<form enctype="multipart/form-data"method="post" action="http://localhost:8086/upload">
	  	<input type="file" name="file"  />
	  	<input type="submit" value="提交" />
	  </form>-->
	  测试修改上传
	  	<input type="file" name="file"  />
	  	<input type="submit" value="提交" v-on:click="upload"/>
  </div>
</template>

<script>
export default {
  name: 'uploadtest',
  methods:{
  	upload:function(){
  		$("[name=file]")
  		var formdata=new window.FormData();
  		formdata.append("file",document.querySelector("input[name=file]").files[0]);
  	
  		
  		this.$http.post("http://localhost:8086/upload",formdata,{
  			headers:{
  				"Content-type":"multipart/form-data"
  			}
  		}).then(function(result){
  			console.log(result);
  			console.log(result.bodyText);
  			alert("文件上传成功");
  			this.$router.go(-1)
  		},function(error){
  			console.log(error.body.message);
  		})
  	
  	}
  }
 
  
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>

<template>
  <div>
    这是：Layout 布局
    <el-upload
      class="upload-demo"
      list-type="picture-card"
      action="https://jsonplaceholder.typicode.com/posts/"
      :on-preview="handlePreview"
      :on-remove="handleRemove"
      :before-remove="beforeRemove"
      multiple
      :limit="3"
      :on-exceed="handleExceed"
      :http-request="onUpload"
      :file-list="fileList">
      <el-button size="small" type="primary">点击上传</el-button>
      <div slot="tip" class="el-upload__tip">只能上传jpg/png文件，且不超过500kb</div>
    </el-upload>
    <span v-for="(item,index) in fileList" :key="index">
      <el-image    style="width: 100px; height: 100px" :src="item.url"></el-image>
    </span>
  </div>
</template>
<script>
  export default {
    data() {
      return {
        fileList: [{name: 'food.jpeg',
          url: 'https://fuss10.elemecdn.com/3/63/4e7f3a15429bfda99bce42a18cdd1jpeg.jpeg?imageMogr2/thumbnail/360x360/format/webp/quality/100'},
          {name: 'food2.jpeg', url: 'https://fuss10.elemecdn.com/3/63/4e7f3a15429bfda99bce42a18cdd1jpeg.jpeg?imageMogr2/thumbnail/360x360/format/webp/quality/100'}]
      };
    },
    methods: {
      onUpload (file) {
        this.fileList.push(file)
        file.url= 'D://anzhuangbao//BlueLava_1112000xx_inspiron_wallpaper58095_16x9_72dpi_RGB//BlueLava.jpg';
        console.log(file, this.fileList );
      } ,
      handleRemove(file, fileList) {
        console.log(file, fileList);
      },
      handlePreview (file) {
       // fileList.add(file);
        console.log(file);
      },
      handleExceed (files, fileList) {
        this.$message.warning(`当前限制选择 3 个文件，本次选择了 ${files.length} 个文件，共选择了 ${files.length + fileList.length} 个文件`) ;
      },
      beforeRemove(file, fileList) {
        return this.$confirm(`确定移除 ${ file.name }？`);
      }
    }
  }
</script>

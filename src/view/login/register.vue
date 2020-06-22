<template>

    <el-dialog
  :visible.sync="dialogVisible"
  class="registre"
  width="600"
  :show-close="false"
  >
   <div slot="title" class="title">用户注册</div>
  <span slot="footer" class="dialog-footer">
    <el-button @click="dialogVisible = false">取 消</el-button>
    <el-button type="primary" @click="dialogVisible = false">确 定</el-button>
  </span>
</el-dialog>

</template>

<script>
export default {
    name:'register',
    data() {
        return {
            dialogVisible: false
        }
    },
}
</script>

 <style lang="less">
    .registre{
        .title{
           height: 53px;
           background-color: rgba(3, 192, 249, 1);
           text-align: center;
           color: #fff;
           line-height: 53px;
        }
        .el-dialog__header{
            padding: 0;
        }
    }
</style>

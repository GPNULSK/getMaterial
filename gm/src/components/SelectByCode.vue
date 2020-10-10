<template>
  <div>

    <el-container>
      <el-header>
        <el-page-header @back="goBack" >
        </el-page-header>
      </el-header>
      <el-main style="padding: 0">
        <span>物料代码:</span>
        <el-input v-model="materialCode"   style="width: 200px" size="mini" placeholder="请输入内容"></el-input>
        <br><br>
        <div class="table_div">
          <el-table
            :data="tableData"
            border
            size="mini"
            @row-click="getCurId"
            :show-header="false"
            style="width: 100%;">
            <el-table-column
              label="编号"
              prop = "id"
              align="center">
            </el-table-column>
          </el-table>
        </div>
      </el-main>
    </el-container>

  </div>
</template>

<script>
  import Bus from '../common/bus'
    export default {
        name: "SelectByCode",
      data(){
          return{
            materialCode: '',
            materialName:'物料名称',
            materialType:'96',
            union:'个',
            tableData:[
              {id:'12'},
              {id:'45'}
            ]
          }
      },

      methods: {
        getCurId(row){
          this.materialCode=row.id;
          this.materialName='五厘米',
            this.materialType='类别',
            this.union='个'

          // this.axios("http://localhost:8080/xx",{
          //   params:{
          //     id:materialCode
          //   }
          // }).then(res=>{
          //
          // })
          this.$router.push({
            path:'/applyMain',
            query: {
              materialCode:this.materialCode,
              materialName:this.materialName,
              materialType:this.materialType,
              union:this.union
            }
          })
        },

        goBack(){
          this.$router.go(-1)
        }
      }

    }
</script>

<style scoped>


</style>

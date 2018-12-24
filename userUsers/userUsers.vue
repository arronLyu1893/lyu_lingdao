<template>
  <div class="panel panel-default">
    <div class="panel-heading">
      <h3 class="panel-title">用户管理</h3>
    </div>
    <div class="panel-body">
      <div class="col-sm-12">
        <ul class="nav nav-tabs">
          <li class="active">
            <a href="#">
              <span class="visible-xs"></span>
              <span class="hidden-xs">用户管理</span>
            </a>
          </li>           
        </ul>
        <div class="tab-content  p-0 m-t-15">
          <el-col :span="4">
            <el-tree :data="data" :props="defaultProps" @node-click="handleNodeClick"></el-tree>
          </el-col>
          <el-col :span="20">
            <el-col :span="24">鸿合科技-信息部</el-col>

            <el-row>
              <el-col :span="6">
                <el-input v-model="input" placeholder="请输入内容"></el-input>
              </el-col>
              <el-col :span="3">
                <el-button>默认按钮</el-button>
              </el-col>   
            </el-row>
            <el-row>
              <el-table
                ref="multipleTable"
                :data="tableData3"
                tooltip-effect="dark"
                style="width: 100%"
                @selection-change="handleSelectionChange">
                <el-table-column
                  type="selection"
                  width="55">
                </el-table-column>
                <el-table-column
                  label="日期"
                  width="120">
                  <template slot-scope="scope">{{ scope.row.date }}</template>
                </el-table-column>
                <el-table-column
                  prop="name"
                  label="姓名"
                  width="120">
                </el-table-column>
                <el-table-column
                  prop="address"
                  label="地址"
                  show-overflow-tooltip>
                </el-table-column>
              </el-table>
              <div style="margin-top: 20px">
                <el-button @click="toggleSelection([tableData3[1], tableData3[2]])">切换第二、第三行的选中状态</el-button>
                <el-button @click="toggleSelection()">取消选择</el-button>
              </div>
            </el-row>


          </el-col>
        </div>
        
      </div>
    </div>
  </div>
</template>
<script>
  export default {
    data () {
      return {
        data: [{ 
          label: '鸿合科技-信息部',
          children: [{
            label: '鸿合科技信息部',
            children: [{
              label: 'flag'
            }]
          },{
            label: '123',
            children: [{
              label: '斤斤计较'
            }]
          }]
        }, {
          label: '一级 2',
          children: [{
            label: '二级 2-1',
            children: [{
              label: '三级 2-1-1'
            }]
          }, {
            label: '二级 2-2',
            children: [{
              label: '三级 2-2-1'
            }]
          }]
        }, {
          label: '一级 3',
          children: [{
            label: '二级 3-1',
            children: [{
              label: '三级 3-1-1'
            }]
          }, {
            label: '二级 3-2',
            children: [{
              label: '三级 3-2-1'
            }]
          }]
        }],
        defaultProps: {
          children: 'children',
          label: 'label'
        }
      }

    }
  }
</script>
<style>
  .panel .panel-body {
    padding:20px;
  }
  .panel-default>.panel-heading {
    color: #797979;
    background-color: #fafafa;
  }
  .panel-heading {
    border-radius: 0;
    border: none !important;
    padding: 10px 20px;
  }
  .nav {
    padding-left: 0;
    margin-bottom: 0;
    list-style: none;
  }
  .nav.nav-tabs {
    border-bottom: 1px solid #ddd;
  }
  .tab-content {
    color: #666;
  }
  .m-t-15 {
    margin-top: 15px;
  }
</style>
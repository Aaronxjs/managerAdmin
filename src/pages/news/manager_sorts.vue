<template>
  <el-table
    :data="tableData.filter(data => !search || data.name.toLowerCase().includes(search.toLowerCase()))"
    row-key="id"
    border
    lazy
    :tree-props="{children: 'children', hasChildren: 'hasChildren'}"
    style="width: 100%">
    <el-table-column
      align="center"
      :label="tableTitle.name"
      prop="name">
    </el-table-column>
    <el-table-column
      align="center"
      :label="tableTitle.sortRank"
      prop="sortRank">
    </el-table-column>
    <el-table-column
      align="center"
      :label="tableTitle.createTime"
      prop="createTime">
    </el-table-column>
    <el-table-column
      align="center"
      :label="tableTitle.creator"
      prop="creator">
    </el-table-column>
    <el-table-column
      align="right">
      <template slot="header" slot-scope="scope">
        <el-input
          v-model="search"
          size="mini"
          placeholder="输入分类名称关键字搜索" class="search"/>
      </template>
      <template slot-scope="scope">
        <el-button
          size="mini"
          @click="handleEdit(scope.$index, scope.row)">Edit</el-button>
        <el-button
          size="mini"
          type="danger"
          @click="handleDelete(scope.$index, scope.row)">Delete</el-button>
      </template>
    </el-table-column>
  </el-table>
</template>
<script>
export default {
    data() {
        return {
            tableData: [{
                id: 1,
                name: '公司动态',
                sortRank: 1,
                createTime: '2019-08-02',
                creator: 'admin',
                children: [
                  {
                    id: 11,
                    name: '公司动态',
                    sortRank: 2,
                    createTime: '2019-08-02',
                    creator: 'admin'
                  },
                  { 
                    id: 12,               
                    name: '公司动态',
                    sortRank: 2,
                    createTime: '2019-08-02',
                    creator: 'admin'
                  }
                ]
            }, {
                id: 2,
                name: '行业动态',
                sortRank: 1,
                createTime: '2019-08-02',
                creator: 'admin'
            }],
            tableTitle: {
                name: '分类名称',
                sortRank: '分类级别',
                createTime: '创建时间',
                creator: '创建者'
            },
            search: ''
        }
    },
    methods: {
      load(tree, treeNode, resolve) {
        console.log(tree, treeNode, resolve)
        // setTimeout(() => {
        //     ([
        //     {
        //       id: 11,
        //       name: '公司动态',
        //       sortRank: 2,
        //       createTime: '2019-08-02',
        //       creator: 'admin'
        //     },
        //     {        
        //       id: 22,        
        //       name: '公司动态',
        //       sortRank: 2,
        //       createTime: '2019-08-02',
        //       creator: 'admin'
        //     }
        //   ])
        // }, 1000)
      },
      handleEdit(index, row) {
          console.log(index, row);
      },
      handleDelete(index, row) {
          console.log(index, row);
      }
    }
}
</script>
<style lang="scss" scoped>

</style>

<template>
  <div>
    <el-button size="mini" type="success" @click="toggle">打开Dialog</el-button>
    <el-button size="mini" type="danger" @click="toggleTable">
      打开嵌套表格的Dialog
      <i class="el-icon-success"></i>
    </el-button>
    <el-dialog title="提示" :visible.sync="dialogVisible" width="30%" :before-close="handleClose">
      <span style="display:block;font-size:29px;">这是一段提示信息</span>
      <el-form label-width="80px" label-position="left">
        <el-form-item label="姓名:">
          <el-input v-model="input" style="width:400px"></el-input>
        </el-form-item>
        <el-form-item label="物流详情:">
          <el-input v-model="input" style="width:400px"></el-input>
        </el-form-item>
        <el-form-item label="退货地址:">
          <el-input v-model="input" style="width:400px"></el-input>
        </el-form-item>
        <el-form-item label="详细地址:">
          <el-input v-model="input" style="width:400px"></el-input>
        </el-form-item>
        <el-form-item label="详细地址:">
          <el-select v-model="input" style="width:200px"></el-select>
        </el-form-item>
      </el-form>
      <!-- <el-input style="width:200px" placeholder="请输入内容" size="small"></el-input>
      <span>这也是一段消息</span>-->

      <span slot="footer" class="dialog-footer">
        <el-button @click="dialogVisible = false">取 消</el-button>
        <el-button type="primary" @click="dialogVisible = false">确 定</el-button>
      </span>
    </el-dialog>

    <el-dialog title="提示" :visible.sync="dialogVisible1" width="50%" :before-close="handleClose">
      <span style="display:block;font-size:29px;text-align:center;margin-bottom:20px;">这是一段提示信息</span>

      <el-table :data="tableData" border stripe>
        <el-table-column prop="date" label="时间"></el-table-column>
        <el-table-column label="地址">
          <template slot-scope="scope">
            <p>{{scope.row.address}}</p>
          </template>
        </el-table-column>
        <el-table-column prop="name" label="姓名"></el-table-column>
        <el-table-column type="selection" @change="select"></el-table-column>
        <el-table-column label="操作">
          <template slot-scope="scope">
            <el-switch v-model="value" @change="test"></el-switch>
          </template>
        </el-table-column>
      </el-table>
      <span slot="footer" type="flex" class="dialog-footer">
        <el-button size="mini" @click="dialogVisible1 = false">取 消</el-button>
        <el-button size="mini" type="primary" @click="dialogVisible1 = false">确 定</el-button>
      </span>
    </el-dialog>
    <div class="block">
      <span class="demonstration">默认</span>
      <el-date-picker
        v-model="value1"
        size="mini"
        type="date"
        @change="selectdate"
        placeholder="选择日期"
      ></el-date-picker>
    </div>
    <div>
      <el-button :type="activenum==1?'primary':'info'" size="mini" @click="()=>activenum=1">点击</el-button>
      <el-button :type="activenum==2?'primary':'info'" size="mini" @click="()=>activenum=2">点击</el-button>
      <el-button :type="activenum==4?'primary':'info'" size="mini" @click="()=>activenum=4">点击</el-button>
      <el-button :type="activenum==5?'primary':'info'" size="mini" @click="()=>activenum=5">点击</el-button>
      <el-button :type="activenum==6?'primary':'info'" size="mini" @click="()=>activenum=6">点击</el-button>
    </div>
  </div>
</template>
<script>
export default {
  data() {
    return {
      msg: 124,
      dialogVisible: false,
      dialogVisible1: false,
      input: "",
      value: true,
      value1: "",
      activenum:2,
      tableData: [
        {
          date: "2016-05-02",
          name: "王小虎",
          address: "上海市普陀区金沙江路 1518 弄"
        },
        {
          date: "2016-05-04",
          name: "王小虎",
          address: "上海市普陀区金沙江路 1517 弄"
        },
        {
          date: "2016-05-01",
          name: "王小虎",
          address: "上海市普陀区金沙江路 1519 弄"
        },
        {
          date: "2016-05-03",
          name: "王小虎",
          address: "上海市普陀区金沙江路 1516 弄"
        }
      ]
    };
  },
  methods: {
    toggle() {
      this.dialogVisible = !this.dialogVisible;
    },
    toggleTable() {
      this.dialogVisible = !this.dialogVisible;
    },
    test(e) {
      console.log(e);
    },
    selectdate(e) {
      console.log(e);
    },
    select(e) {
      console.log(e);
    },
    handle(index, row) {
      console.log(row, index);
    },
    handleClose(done) {
      this.$confirm("确认关闭？")
        .then(res => {
          done();
        })
        .catch(err => {});
    }
  }
};
</script>
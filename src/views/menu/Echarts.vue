<template>
    <div>
    <h1>VUE+PowerBI</h1>
    <div>
        <label>部店：</label>
        <el-select v-model="value1" multiple placeholder="選択してください">
            <el-option
            v-for="item in shops"
            :key="item.value"
            :label="item.label"
            :value="item.value">
            </el-option>
        </el-select>
        &nbsp;&nbsp;&nbsp;&nbsp;

        <label>項目：</label>
        <el-select v-model="value2" multiple placeholder="選択してください">
            <el-option
            v-for="item in items"
            :key="item.value"
            :label="item.label"
            :value="item.value">
            </el-option>
        </el-select>
    </div>


    <div class="block" style="margin-top:20px">
        <span class="demonstration">日付：</span>
        <el-date-picker
        v-model="value3"
        type="daterange"
        range-separator="～"
        start-placeholder="開始日"
        end-placeholder="終了日">
        </el-date-picker>
    </div>

    <div style="margin-top:20px;text-align:right">
        <el-button icon="el-icon-delete" type="warning">クリア</el-button>
        <el-button icon="el-icon-search" type="primary">検索</el-button>
    </div>

    <hr></hr>

    <iframe 
    width="1140" 
    height="541.25" 
    src="https://app.powerbi.com/reportEmbed?reportId=2bdf479a-6a67-4e97-b9f7-b4cfac62f63f&autoAuth=true&ctid=6ca86b00-31f7-4ec8-adff-4b1e17898654&config=eyJjbHVzdGVyVXJsIjoiaHR0cHM6Ly93YWJpLWphcGFuLWVhc3QtcmVkaXJlY3QuYW5hbHlzaXMud2luZG93cy5uZXQvIn0%3D" 
    frameborder="0" 
    allowFullScreen="true"
    ></iframe>

    </div>
</template>

<script>
  export default {
    data() {
      return {
        shops: [{
          value: 'n39',
          label: '新富町支店'
        }, {
          value: 'n40',
          label: '日本橋支店'
        }, {
          value: 'n41',
          label: '三越前支店'
        }, {
          value: 'n42',
          label: '旭川支店'
        }],
        items: [{
          value: 'mockA',
          label: 'モック証券A'
        }, {
          value: 'mockB',
          label: 'モック証券B'
        }, {
          value: 'mockC',
          label: 'モック証券C'
        }, {
          value: 'mockD',
          label: 'モック証券D'
        }],
        pickerOptions: {
          shortcuts: [{
            text: '最近一周',
            onClick(picker) {
              const end = new Date();
              const start = new Date();
              start.setTime(start.getTime() - 3600 * 1000 * 24 * 7);
              picker.$emit('pick', [start, end]);
            }
          }, {
            text: '最近一个月',
            onClick(picker) {
              const end = new Date();
              const start = new Date();
              start.setTime(start.getTime() - 3600 * 1000 * 24 * 30);
              picker.$emit('pick', [start, end]);
            }
          }, {
            text: '最近三个月',
            onClick(picker) {
              const end = new Date();
              const start = new Date();
              start.setTime(start.getTime() - 3600 * 1000 * 24 * 90);
              picker.$emit('pick', [start, end]);
            }
          }]
        },
        value1: [],
        value2: [],
        value3: []
      }
    }
  }
</script>

<style>
.item{
    margin-left:'30px'
}
</style>

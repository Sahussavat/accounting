<template>
  <div>
      <table>
          <thead>
              <tr>
                  <th>วัน/เดือน/ปี</th>
                  <th>รายรับ</th>
                  <th>รายจ่าย</th>
                  <th>รวม</th>
                  <th>รายละเอียด</th>
              </tr>
          </thead>
          <tbody>
              <tr v-for="(dateData, i) in dateList " :key="i">
                  <td>{{DateManage.getDate(dateData)}}</td>
                  <td>{{dateData.income}}</td>
                  <td>{{dateData.expense}}</td>
                  <td>{{DateManage.getTotal(dateData)}}</td>
                  <td>{{dateData.detail}}</td>
              </tr>
          </tbody>
      </table>
      <p>รวมเป็นเงิน {{total.amount}}</p>
  </div>
</template>

<script>
import ACM from '@/store/AccountingManage'
import DateManage from '@/store/DateDataManage.js'
export default {
    data(){
        return{
            dateList: [],
            DateManage,
            total: 0
        }
    },
    created(){
        this.fetchDateData()
    },
    methods:{
        fetchDateData(){
            ACM.dispatch('fetchSetOfData')
            this.dateList = ACM.getters.dateDataList
            this.total = ACM.getters.accountTotal
            ACM.dispatch('updateTotal')
        }
    }
}
</script>

<style>

</style>
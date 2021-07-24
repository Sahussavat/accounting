<template>
  <div class="home">
    <AccoutingTable></AccoutingTable>
    <AccoutingForm></AccoutingForm>
  </div>
</template>

<script>
// @ is an alias to /src
import AccoutingTable from '@/components/AccountingTable.vue'
import AccoutingForm from '@/components/AccountingForm.vue'
export default {
  name: 'Home',
  components: {
    AccoutingTable,
    AccoutingForm
  }
}
</script>

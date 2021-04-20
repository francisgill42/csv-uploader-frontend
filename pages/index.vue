<template>
<v-data-table
:headers="headers"
:items="data.data"
class="elevation-1"
:server-items-length="data.total"
:loading="loading"
:search="search"
@pagination="paginate"   

>

  <!-- <template v-slot:top>
  <v-toolbar class="mt-15" app>
  <v-text-field   
  label="Search"
  class="mx-4"
  hide-details v-model="search"
  ></v-text-field>

  </v-toolbar>

  </template> -->




  <template v-slot:item.actions="{ item }">

  <v-icon
  small
  class="mr-2"
  @click="viewItem(item.id)"
  >
  mdi-eye
  </v-icon>

  </template>


</v-data-table>
</template>
<script>
export default {
layout:'web',  
data () {
return {
search : '',  
loading: true,
headers: [

{ text: 'Company Name', value: 'entity_name' },
{ text: 'Date', value: 'registration_incorporation_date' },
// { text: 'paid_up_capital1_ordinary', value: 'paid_up_capital1_ordinary' },
// { text: 'uen_of_audit_firm1', value: 'uen_of_audit_firm1' },
// { text: 'name_of_audit_firm1', value: 'name_of_audit_firm1' },
// { text: 'address_type', value: 'address_type' },
{ text: 'Address', value: 'street_name' },

{ text: 'Action', value: 'actions' },
// { text: 'building_name', value: 'building_name' },
// { text: 'block', value: 'block' },
// { text: 'unit_no', value: 'unit_no' },
// { text: 'company_type_description', value: 'company_type_description' },
// { text: 'primary_ssic_code', value: 'primary_ssic_code' },
// { text: 'primary_ssic_description', value: 'primary_ssic_description' },
// { text: 'secondary_ssic_code', value: 'secondary_ssic_code' },
// { text: 'secondary_ssic_description', value: 'secondary_ssic_description' },

],
data: [],
}
},
mounted(){},

methods : {

paginate(e){ this.getData(e) },

  getData(e){
  this.loading = true
  this.$axios.get(`record?page=${e.page}`, {params : { 'request_per_page' :  e.itemsPerPage }}).then(res => {
  this.data = res.data
  this.loading = false
  });
}
,



viewItem(id) {
this.$router.push('/records/' + id);
}
}
}
</script>
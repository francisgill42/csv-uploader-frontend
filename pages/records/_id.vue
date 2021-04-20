<template>

<div class="mt-10">
  <v-avatar color="primary white--text" size="56">{{ c_name }}</v-avatar>
  <span class="ml-2"> {{ item.entity_name }} </span>

      <v-toolbar flat class="mt-5">
    
        <v-toolbar-title> General Information </v-toolbar-title>

      </v-toolbar>    


  <v-card>

    
  <v-simple-table>

   
    <template v-slot:default>



      <tbody>

            <tr>
            <th class="text-left">
            entity_name
            </th>
            <td>{{ item.entity_name }}</td>
            </tr> 


            <tr>
            <th class="text-left">
            registration_incorporation_date
            </th>

            <td>{{ item.registration_incorporation_date }}</td>
            </tr>

            <tr>
            <th class="text-left">
            paid_up_capital1_ordinary
            </th>

            <td>{{ item.paid_up_capital1_ordinary }}</td>
            </tr>


            <tr>
            <th class="text-left">
            uen_of_audit_firm1
            </th>

            <td>{{ item.uen_of_audit_firm1 }}</td>
            </tr>

            <tr>
            <th class="text-left">
            name_of_audit_firm1
            </th>

            <td>{{ item.name_of_audit_firm1 }}</td>
            </tr>

            <tr>
            <th class="text-left">
            address_type
            </th>

            <td>{{ item.address_type }}</td>
            </tr>

            <tr>
            <th class="text-left">
            street_name
            </th>

            <td>{{ item.street_name }}</td>
            </tr>

            <tr>
            <th class="text-left">
            building_name
            </th>

            <td>{{ item.building_name }}</td>
            </tr>

            <tr>
            <th class="text-left">
            block
            </th>

            <td>{{ item.block }}</td>
            </tr>

            <tr>
            <th class="text-left">
            unit_no
            </th>
            <td>{{ item.unit_no }}</td>

            </tr>

            <tr>
            <th class="text-left">
            company_type_description
            </th>
            <td>{{ item.company_type_description }}</td>

            </tr>

            <tr>
            <th class="text-left">
            primary_ssic_code
            </th>
            <td>{{ item.primary_ssic_code }}</td>

            </tr>

            <tr>
            <th class="text-left">
            primary_ssic_description
            </th>
            <td>{{ item.primary_ssic_description }}</td>

            </tr>

            <tr>
            <th class="text-left">
            secondary_ssic_code
            </th>
            <td>{{ item.secondary_ssic_code }}</td>

            </tr>

            <tr>
            <th class="text-left">
            secondary_ssic_description
            </th>
            <td>{{ item.secondary_ssic_description }}</td>

            </tr>

      </tbody>
     
    </template>
  </v-simple-table>
      </v-card>

  </div>

</template>
<script>
  export default {
    layout : 'web',
    data () {
      return {
        item: {},
        c_name : '',

       }
    },
    computed : {
       getFirstCharacter () {

      }
    },
    created(){
            this.$axios.get('record/' + this.$route.params.id)
                .then(res => {
                  this.item = res.data
                  this.c_name = res.data.entity_name.charAt(0)
                }).catch(e => console.log(e))
    },
  }
</script>
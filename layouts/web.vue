<template>
<v-app>

<v-app-bar app dark>
<span style="width:175px;" class="ma-5">
  <v-img src="https://d3tlirhs5wvpe9.cloudfront.net/recordowl_logo.png" alt="" />
</span>

<span class="mt-2">
    <v-btn to="/" small>Home</v-btn>
</span>

<span class="mt-2 ml-3 ">
    <v-btn to="/records" small>Company</v-btn>
</span>



</v-app-bar>
<v-main>

<v-container>
<nuxt />
</v-container>

</v-main>

<v-footer :fixed="fixed" app dark>
<span>&copy; {{year}}</span> 
</v-footer>
</v-app>
</template>

<script>
export default {

data () {
return {
year: new Date().getFullYear(),
clipped: false,
fixed:false,
drawer: true,
menus : [],      

miniVariant: false,
right: true,
rightDrawer: false,
title: 'Virtual School',
logout_btn:{
icon:'mdi-logout',
label:'Logout'
}
}
},
created () {
  this.get_menus();
},
methods:{
async logout() {
  await this.$auth.logout();
},
get_menus () {

  var menu = [
            { icon: 'mdi-apps', title: 'Home',to: '/' },
            
  ];

  this.menus = menu;

  



}
}
}
</script>

<style>
/* .grad {
  background: linear-gradient(to bottom right, orange, grey);
} */
</style>

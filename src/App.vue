<template>
  <div id="app">

    <transition name="fade" mode="out-in">
      <router-view></router-view>
    </transition>

  </div>
      <!-- /#app -->
</template>

<script>
  export default {

    created() {
      //запись из api to vuex
      if(this.$store.state.staff.length == 0){
        console.log("staff is empty. load staff from api App.vue")

        this.resource = this.$resource('staff')
        this.resource.get().then(response => response.json())
        .then(staff => this.$store.dispatch('assyncSetStaff', staff))
      }

    }
  }
</script>
<template>
  <div class="hello">
    <!-- <h1>{{ msg }}</h1> -->
    <!-- Navbar -->
    <div>
      <b-navbar toggleable="lg" type="dark" variant="info">
        <b-navbar-brand href="#">
          <img src="@/assets/logo.png" alt="Kitten" style="width: 203px; height: 60px">
        </b-navbar-brand>

        <b-navbar-toggle target="nav-collapse"></b-navbar-toggle>

        <b-collapse id="nav-collapse" is-nav>
          <b-navbar-nav>
            <b-nav-item href="#" v-bind:style="{ color: 'yellow' }"><b>Market place</b></b-nav-item>
            <b-nav-item href="#" disabled>About Anh Tuan</b-nav-item>
          </b-navbar-nav>

          <!-- Right aligned nav items -->
          <b-navbar-nav class="ml-auto">
            <b-navbar-nav>
              <b-nav-item href="#">Connect Wallet</b-nav-item>
            </b-navbar-nav>

            <b-nav-item-dropdown text="Lang" right>
              <b-dropdown-item href="#">EN</b-dropdown-item>
              <b-dropdown-item href="#">ES</b-dropdown-item>
              <b-dropdown-item href="#">RU</b-dropdown-item>
              <b-dropdown-item href="#">FA</b-dropdown-item>
            </b-nav-item-dropdown>

            <b-nav-item-dropdown right>
              <!-- Using 'button-content' slot -->
              <template #button-content>
                <em>User</em>
              </template>
              <b-dropdown-item href="#">Profile</b-dropdown-item>
              <b-dropdown-item href="#">Sign Out</b-dropdown-item>
            </b-nav-item-dropdown>
          </b-navbar-nav>
        </b-collapse>
      </b-navbar>
    </div>
    <!-- End Navbar -->
    <!-- Divide Column -->
    <b-container fluid="fluid">
      <b-row class="mt-3">
        <b-col sm="4">
          <SortFilterMecha />
        </b-col>
        <b-col sm="8">
          <ShowMechaToken />
        </b-col>
      </b-row>
    </b-container>
    <!-- End Divine Column -->
  </div>
</template>

<script>
import SortFilterMecha from './SortFilterMecha.vue'
import ShowMechaToken from './ShowMechaToken.vue'
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  components: {
    SortFilterMecha,
    ShowMechaToken
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>

<template>
  <v-app>
      <v-app-bar color="#76C03C" dark style="height: 80px">
        <v-app-bar-nav-icon @click.stop="drawer = !drawer"  style="margin-top: 18px; font-size: 25px;"></v-app-bar-nav-icon>
        <v-toolbar-text class="name" style="margin-top: 18px; font-size: 25px; color:ghostwhite">RemodelKing</v-toolbar-text>
        <v-btn style="margin-top: 18px; font-size: 25px;"> <v-icon>mdi-bell</v-icon> </v-btn>
        <v-spacer></v-spacer>
        <div style="margin-right: 270px; margin-top: 24px;">
          <Languages></Languages>
        </div>

        <router-link to="/UserType" class="text-decoration-none" style="margin-top: 56px; border-style: solid; border-color: black; background-color: #984857;">
          <v-btn id="menu-activator" size="30px" width="120px" color="#FFFFFF"><v-icon>mdi-login-variant</v-icon>
            {{ $t('Log-in') }}</v-btn>
          <v-menu activator="#menu-activator">
            <v-list>
              <v-list-item
                  v-for="(item, index) in items"
                  :key="index"
                  :value="index"
              >
                <v-list-item-title>{{ item.title }}</v-list-item-title>
              </v-list-item>
            </v-list>
          </v-menu>
        </router-link>
        <router-link to="/Register" class="text-decoration-none" style="margin-top: 56px; margin-right: 15px; margin-left: 10px; border-style: solid; border-color: black; background-color: #984857">
          <v-btn size="30px" width="120px" color="#FFFFFF"><v-icon>mdi-account-plus</v-icon>  {{ $t('Register') }}</v-btn>
        </router-link>
        <span><img :src="logo" style="height: 65px; margin-top:25px; border-style: dot-dot-dash;"/></span>
      </v-app-bar>
      <v-navigation-drawer v-model="drawer" bottom color="#4F8983">
        <v-list bg-color="#4f8983" style="margin-top: 13px">
          <v-list-item :to="{path:'/'}">
            <v-list-item-title>{{ $t('Home') }}</v-list-item-title>
          </v-list-item>
          <v-list-item :to="{path:'/CompanyProgress'}">
            <v-list-item-title>{{ $t('Titles.Company-Progress') }}</v-list-item-title>
          </v-list-item>
          <v-list-item :to="{path:'/client-portfolio'}">
            <v-list-item-title>{{ $t('Titles.Portfolio') }}</v-list-item-title>
          </v-list-item>
          <v-list-item :to="{path:'/business/info/2'}">
            <v-list-item-title>{{ $t('Titles.Your-Business') }}</v-list-item-title>
          </v-list-item>
        </v-list>
      </v-navigation-drawer>
    <br><br><br><br>
    <router-view/>
  </v-app>
  <footer-component class="footer" />
</template>

<script>
import logo from "./assets/logo.png";
import footerComponent from "./components/footerComponent.vue";
import Languages from "./components/Languages.vue";

export default {
  components:{
    Languages,
    footerComponent
  },

  data: () => ({
    drawer: false,
    logo: logo,
    items: [
      {
        title:'Business'
      },
      {
        title:'Client'
      }
    ]
  }),
}
</script>

<style>
  .name{
    font-size: 25px;
    padding-right: 25px;
  }
</style>

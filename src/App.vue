<template>
  <v-app>
    <v-card
            color="grey lighten-4"
            flat
            height="100%"
            tile
    >
    <v-navigation-drawer
            app
            temporary
            v-model="drawer"
    >
      <v-list>
        <v-list-item
                v-for="link of links"
                :key="link.title"
                :to="link.url"
        >
          <v-list-item-icon>
            <v-icon>{{link.icon}}</v-icon>
          </v-list-item-icon>
          <v-list-item-content>
            <v-list-item-title v-text="link.title"></v-list-item-title>
          </v-list-item-content>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>

      <v-toolbar dark color="primary" >
        <v-app-bar-nav-icon
                @click="drawer = !drawer"
                class="hidden-md-and-up"
        ></v-app-bar-nav-icon>

        <v-toolbar-title>
          <router-link to="/" tag="span" class="pointer">Ad application</router-link>
        </v-toolbar-title>

        <v-spacer></v-spacer>
        <v-toolbar-items class="hidden-sm-and-down">
          <v-btn
                  x-large
                  text
                  v-for="link in links"
                  :key="link.title"
                  :to="link.url"
          >
            <v-icon left>{{link.icon}}</v-icon>
            {{link.title}}
          </v-btn>
        </v-toolbar-items>

        <!--<v-btn icon>-->
          <!--<v-icon>mdi-heart</v-icon>-->
        <!--</v-btn>-->

        <!--<v-btn icon>-->
          <!--<v-icon>mdi-dots-vertical</v-icon>-->
        <!--</v-btn>-->
      </v-toolbar>


    <v-content>
      <router-view></router-view>
    </v-content>
    </v-card>
  </v-app>
</template>

<script>
//import HelloWorld from './components/HelloWorld';

export default {
    data: () => ({
        drawer: false,
        links: [
            {title: 'Login', icon: 'mdi-lock', url: '/login'},
            {title: 'Registration', icon: 'mdi-face', url: '/registration'},
            {title: 'Orders', icon: 'mdi-bookmark-outline', url: '/orders'},
            {title: 'New ad', icon: 'mdi-note-plus', url: '/new'},
            {title: 'My ads', icon: 'mdi-format-list-bulleted', url: '/list'}
        ],
        items: [
            { icon: true, title: 'Jason Oner', avatar: 'https://cdn.vuetifyjs.com/images/lists/1.jpg' },
            { title: 'Travis Howard', avatar: 'https://cdn.vuetifyjs.com/images/lists/2.jpg' },
            { title: 'Ali Connors', avatar: 'https://cdn.vuetifyjs.com/images/lists/3.jpg' },
            { title: 'Cindy Baker', avatar: 'https://cdn.vuetifyjs.com/images/lists/4.jpg' },
        ]
    }),
};
</script>

<style scoped>
  .pointer{
    cursor: pointer;
  }
</style>

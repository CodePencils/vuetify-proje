<template>
  <v-app>
    <v-navigation-drawer v-model="drawer" app clipped flating temporary>
      <v-list dense>
        <v-row class="ma-2 mb-3"> 
            <v-icon class="mx-4" dark color="red" large>mdi-video</v-icon>
            <v-toolbar-title class="aling-center">
              <router-link  style="text-decoration: none; color: inherit;" to="/">
                <span class="title">YouTech</span>
              </router-link>
            </v-toolbar-title> 
        </v-row>
        <v-list-item v-for="item in items" :key="item.Icon" link to="/About">
          <v-list-item-action>
            <v-icon>{{ item.Icon }}</v-icon>
          </v-list-item-action>
          <v-list-item-content>
            <v-list-item-title>{{ item.Text }}</v-list-item-title>
          </v-list-item-content>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>
    <v-app-bar app clipped-left>
      <v-app-bar-nav-icon @click="drawer = !drawer" />
      <v-list-item > 
        <v-icon class="mx-4" dark color="red" large>mdi-video</v-icon>
        <v-toolbar-title class="aling-center">
            <router-link  style="text-decoration: none; color: inherit;" to="/">
                <span class="title">YouTech</span>
              </router-link> 
        </v-toolbar-title> 
      </v-list-item>
      <v-spacer />
      <v-text-field
        placeholder="Ara..."
        class="mt-7"
        solo
        single-line
        append-icon="mdi-magnify"
        color="white"
      />
      <v-spacer />
      <v-btn class="ml-0" color="cyan" icon><v-icon>mdi-apps</v-icon></v-btn>
      <v-btn class="ma-2" color="orange" icon><v-icon>mdi-bell</v-icon></v-btn>
      <div>
        <v-menu
          v-model="menu"
          :close-on-content-click="false"
          :nudge-width="250"
          offset-x
        >
          <template v-slot:activator="{ on }">
            <v-avatar size="40">
              <!-- <img v-on="on" src="assets/logo.svg"/> -->
              <v-img
                v-on="on"
                lazy-src="/assets/user.png"
                max-height="150"
                max-width="250"
                src="./assets/user.png"
              ></v-img>
            </v-avatar>
          </template>
          <v-card>
            <v-list>
              <v-list-item>
                <v-list-item-avatar></v-list-item-avatar>
                <v-list-item-content>
                  <v-list-item-title>Emre Kara</v-list-item-title>
                  <v-list-item-subtitle>Resmi Hesap</v-list-item-subtitle>
                </v-list-item-content>
              </v-list-item>
            </v-list>
            <v-divider />
            <v-list>
              <v-list-item>
                <v-list-item-action>
                  <v-icon>mdi-cog</v-icon>
                </v-list-item-action>
                <v-list-item-title>Ayarlar</v-list-item-title>
              </v-list-item>
            </v-list>
            <v-list>
              <v-list-item>
                <v-list-item-action>
                  <v-switch v-model="theme" color="purple"></v-switch>
                </v-list-item-action>
                <v-list-item-title>Karanlık Tema</v-list-item-title>
              </v-list-item>
            </v-list>
            <v-card-actions>
              <v-spacer />
              <v-btn color="primary right" text @click="menu = false">
                Çıkış Yap
              </v-btn>
            </v-card-actions>
          </v-card>
        </v-menu>
      </div>
    </v-app-bar>
    <v-main>
      <router-view></router-view>
    </v-main>
  </v-app>
</template>

<script>

export default {
  name: "App",
  data: () => ({
    items: [
      { Icon: "mdi-trending-up", Text: "Popüler içerik" },
      { Icon: "mdi-youtube-subscription", Text: "Takip" },
      { Icon: "mdi-history", Text: "Geçmiş" },
      { Icon: "mdi-playlist-play", Text: "Kaydedilenler" },
      { Icon: "mdi-clock", Text: "Hatırlatıcılar" },
    ],
    menu: false,
    theme: false,
    drawer: false,
  }),
  created() {
    this.theme =
      sessionStorage.getItem("tema") == null
        ? false
        : sessionStorage.getItem("tema") == "false"
        ? false
        : true;
  },
  watch: {
    theme: function (next) {
      this.$vuetify.theme.dark = next;
      sessionStorage.setItem("tema", next);
    },
  },
};
</script>

 
<template>
  <v-app>  
    <v-navigation-drawer v-model="drawer" app clipped flating temporary>
      <v-list dense>
        <v-row class="ma-2 mb-3">
         <v-icon class="mx-4" dark color="red" large>mdi-video</v-icon>
          <v-toolbar-title  class="aling-center">
            <span class="title">YouTech</span>
          </v-toolbar-title>
        </v-row>
        <v-list-item v-for="item in items" :key="item.Icon" link>
          <v-list-item-action>
            <v-icon>{{item.Icon}}</v-icon>
          </v-list-item-action>
          <v-list-item-content>
            <v-list-item-title>{{item.Text}}</v-list-item-title>
          </v-list-item-content>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>
    <v-app-bar app clipped-left>
       <v-app-bar-nav-icon @click="drawer=!drawer" />
       <v-icon class="mx-4" dark color="red" large>mdi-video</v-icon>
       <v-toolbar-title  class="aling-center">
         <span class="title">YouTech</span>
       </v-toolbar-title>
       <v-spacer/>
       <v-text-field placeholder="Ara..." class="mt-7" solo single-line append-icon="mdi-magnify" color="white" />
       <v-spacer/>
      <v-btn class="ml-0" color="cyan" icon><v-icon>mdi-apps</v-icon></v-btn>
      <v-btn class="ma-2" color="orange" icon><v-icon>mdi-bell</v-icon></v-btn>
      <div>
        <v-menu v-model="menu" :close-on-content-click="false" :nudge-width="250" offset-x>
          <template v-slot:activator="{on}">
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
          <v-card >
              <v-list>
                <v-list-item>
                <v-list-item-avatar></v-list-item-avatar>
                <v-list-item-content>
                  <v-list-item-title>Emre Kara</v-list-item-title>
                  <v-list-item-subtitle>Resmi Hesap</v-list-item-subtitle>
                </v-list-item-content>
                </v-list-item>
              </v-list>
              <v-divider/>
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
              <v-spacer/>
                  <v-btn color="primary right"   text @click="menu=false">
                 Çıkış Yap
               </v-btn> 
              </v-card-actions>
          </v-card>
        </v-menu>
      </div>
     </v-app-bar>
     <v-main>
       <v-container>
         <v-row class="mb-4">
           <v-col sm="3" v-for="(item,index) in 12" :key="index">
             <v-card>
               <v-img 
               lazy-src="`https://picsum.photos/10/20?random=${(index+1)}`"
               :src="`https://picsum.photos/500/500?random=${(index+1)}`"
               />
               <v-card-subtitle class="">Number{{item}}</v-card-subtitle>
               <v-card-text class="text--primary"> <div>Başlık Alanı</div> <div>Başlık İçeriği</div> </v-card-text>
               <v-btn sm="2" color="blue" text><v-icon>mdi-content-save</v-icon></v-btn>
               <v-btn sm="2" color="green" text><v-icon>mdi-share-variant</v-icon></v-btn>
               <v-btn sm="2" color="red" text><v-icon>mdi-delete</v-icon></v-btn>
             </v-card>
           </v-col>
         </v-row>
       </v-container>
     </v-main>
  </v-app>
</template>

<script> 

export default {
  name: "App",
  created:function(){
     this.theme = sessionStorage.getItem("DarkTema") || false;
          //  this.$vuetify.theme.dark = true;
  },
  data:()=>({
    items:[
      {Icon:"mdi-trending-up",Text:"Popüler içerik"},
      {Icon:"mdi-youtube-subscription",Text:"Takip"},
      {Icon:"mdi-history",Text:"Geçmiş"},
      {Icon:"mdi-playlist-play",Text:"Kaydedilenler"},
      {Icon:"mdi-clock",Text:"Hatırlatıcılar"},
    ],
    menu:false,
    theme:false,
    drawer:false
  }),
  watch:{
    theme:function(next){
        this.$vuetify.theme.dark = next;
        sessionStorage.setItem("DarkTema",next)
    }
  }
};
</script>

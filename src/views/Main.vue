 <template>
  <v-container>
    <v-row class="mb-4">
      <v-col sm="2" v-for="(item, index) in 12" :key="index">
        <v-card>
          <v-img
            lazy-src="`https://picsum.photos/10/20?random=${(index+1)}`"
            :src="`https://picsum.photos/500/500?random=${index + 1}`"
          />
          <v-card-subtitle class="">Number{{ item }}</v-card-subtitle>
          <v-card-text class="text--primary">
            <div>Başlık Alanı Üst</div>
            <div>Başlık İçeriği</div>
          </v-card-text>
          <v-btn sm="2" color="blue" text
            ><v-icon>mdi-content-save</v-icon></v-btn
          >
          <v-btn sm="2" color="green" text
            ><v-icon>mdi-share-variant</v-icon></v-btn
          >
          <v-btn sm="2" color="red" text><v-icon>mdi-delete</v-icon></v-btn>
        </v-card>
      </v-col>
    </v-row>
  </v-container>
</template>
 
<script>
export default {
  name: "Main",
  created() {},
};
</script>

 
 <style>
</style>

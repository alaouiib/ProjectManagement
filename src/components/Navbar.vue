<template>
  <nav>
    <v-toolbar flat app>
      <v-toolbar-side-icon @click="drawer = !drawer"></v-toolbar-side-icon>
      <v-toolbar-title class=" grey--text">
        <span class="font-weight-light">i</span>
        <span>GARBAGE</span>
      </v-toolbar-title>
      <v-spacer></v-spacer>
        <!-- dropdown menu -->
      <v-menu offset-y>
        <v-btn flat slot="activator" color="grey">
          <v-icon left>expand_more</v-icon>
          <span>Menu</span>
        </v-btn>
        <v-list>
          <v-list-tile v-for="link in links" :key="link.text" router :to="link.route">
            <v-list-tile-title>{{ link.text }}</v-list-tile-title>
          </v-list-tile>
        </v-list>
      </v-menu>

      <v-btn flat>
        <span>SIGN OUT</span>
        <v-icon flat right>exit_to_app</v-icon>
      </v-btn>
          </v-toolbar>

      
    <v-navigation-drawer app v-model="drawer" class="primary">
      <v-layout column align-center>
        <v-flex class="pt-5"> 
                

          <v-avatar size="100" class="grey lighten-2">
            <image-uploader
        
        :maxHeight="98"
        :preview="false"
        :className="['fileinput', { 'fileinput--loaded': hasImage }]"
        capture="environment"
        :debug="1"
        doNotResize="gif"
       
        outputFormat="verbose"
        @input="setImage"
         >
        <label for="fileInput" slot="upload-label" >

           <img v-if="!hasImage"   src="/avatar-2.png" >
           <div v-if = "hasImage" >
             <img :src="image.dataUrl" />
           </div>
            
<!-- 
        <span class="upload-caption">{{
                    hasImage ? "Replace" : "Click to upload"
                  }}
        </span> -->

        </label>

      </image-uploader>
          </v-avatar>

          <p class="white--text subheading mt-1">Abdelhamid Alaoui</p>
        </v-flex>
      </v-layout>
      <v-list>
        <v-list-tile v-for="link in links" :key="link.text" router :to="link.route">
          <v-list-tile-action>
            <v-icon class="white--text">{{ link.icon }}</v-icon>
          </v-list-tile-action>
          <v-list-tile-content>
            <v-list-tile-title class="white--text">{{ link.text }}</v-list-tile-title>
          </v-list-tile-content>
        </v-list-tile>
      </v-list>
</v-navigation-drawer>

  </nav>
</template>
<script>
export default {
  data() {
    return {
      drawer: false,
      links: [
        { icon: 'dashboard', text: 'Dashboard', route: '/' },
        { icon: 'folder', text: 'My Projects', route: '/projects' },
        { icon: 'person', text: 'Team', route: '/team' },
      ],
      hasImage: false,
      image: null
    }
  },
  methods: {
    setImage: function(output) {
      this.hasImage = true;
      this.image = output;
      console.log(this.image);
      
    }
  }
}
</script>
<style>
  #fileInput {
  display: none;
}
.centered {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
}
.centered:hover {
color: brown
}


</style>
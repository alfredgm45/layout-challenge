<template>
  <v-app class="white">
    <v-navigation-drawer
      v-model="drawer"
      :mini-variant="mini"
      width="170"
      app
      permanent>
      <v-list class="ml-2">
        <v-list-tile avatar
          tag="div">
          <v-list-tile-action>
            <v-btn dark
              icon
              large
              class="mr-2"
              color="red darken-1"
              @click.stop="mini = !mini">
              <v-icon v-show="mini">chevron_left</v-icon>
              <v-icon v-show="!mini">chevron_right</v-icon>
            </v-btn>
          </v-list-tile-action>
        </v-list-tile>
        <v-list-tile-title v-show="!mini"
          class="headline font-weight-medium ml-2 mt-5 mb-4">
          Giselle
        </v-list-tile-title>
      </v-list>
      <v-list dense>
        <v-divider light></v-divider>
        <v-list-tile class="ml-2"
          v-for="(item, index) in items"
          :key="index"
          @click="menuClick"
          @mouseenter="optionHightlight(index)"
          @mouseleave="optionNormal(index)">
          <v-list-tile-content>
            <v-list-tile-title :class="item.weight">{{ item.title }}</v-list-tile-title>
          </v-list-tile-content>
        </v-list-tile>
      </v-list>
    </v-navigation-drawer>
     <v-content>
      <v-container fluid full-height>
         <div class="content">
          <div class="avatar">
            <v-avatar
              size="75px">
              <p class="userName">Giselle</p>
              <v-btn fab top fixed right
                color="grey lighten-2"></v-btn>
            </v-avatar>
          </div>
          <div class="middleContent mt-3">
            <p class="display-2 text-xs-center font-weight-medium">Your account</p>
            <p class="subheading mt-2 text-xs-center grey--text lighten-1 font-weight-regular">Tell us a litle more about yourself</p>
          </div>
        </div>
      </v-container>
      <v-divider class="mt-4"></v-divider>
      <div class="form">
        <v-form>
          <p class="body-2 font-weight-bold mt-5">Personal information</p>
          <v-text-field
            class="mt-5"
            color="black"
            v-for="(item, index) in formInputs"
            :key="index"
            :label="item.label"
          ></v-text-field>
          <v-select
            class="mb-5 mt-5"
            color="black"
            :items="countries"
            label="Country"
          ></v-select>
        </v-form>
      </div>
    </v-content>
  </v-app>
</template>
<script>
export default {
  name: 'HelloWorld',
  data () {
    return {
      drawer: true,
      countries: ['United states', 'Venezuela', 'Argentina'],
      items: [
        { title: 'ACCOUNT', weight: '' },
        { title: 'Career', weight: '' },
        { title: 'Personal', weight: '' },
        { title: 'MANAGE', weight: '' },
        { title: 'Password', weight: '' },
        { title: 'Email', weight: '' }
      ],
      mini: false,
      formInputs: [
        {label: 'First name'},
        {label: 'Last name'},
        {label: 'Phone'}
      ]
    }
  },
  methods: {
    menuClick () {
      console.log('Click event of the menu')
    },
    /** highlights the option on the right menu when the mouse is over this one
     * @param {Number} Option index on the left menu
     */
    optionHightlight (index) {
      this.items[index].weight = 'font-weight-bold'
    },
    /**
     * Takes off the highlighted on the option selected
     * @param {Number} Option index on the left menu
     */
    optionNormal (index) {
      this.items[index].weight = ''
    }
  }
}
</script>
<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
/* Css grid */
.content {
  display: grid;
  grid-template-rows: auto auto auto;
}
.avatar {
  display: grid;
  justify-content: end;
  margin-right: 60px;
}
.userName {
  position: fixed;
  top: 35px;
}
.middleContent {
  display: grid;
  justify-content: center;
}
.form {
  display: grid;
  grid-template-columns: 350px;
  justify-content: center;
}
/* Reduces the size of the form when the screen size is for mobile */
@media (max-width: 600px) {
  .form {
    display: grid;
    grid-template-columns: 150px;
    justify-content: center;
  }
}
</style>

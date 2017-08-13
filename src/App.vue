<template>
  <v-app dark>
    <v-navigation-drawer
      persistent
      :mini-variant="miniVariant"
      :clipped="clipped"
      v-model="drawer"
      enable-resize-watcher
    >
      <v-flex xs12>
        <v-card class="blue-grey darken-2 white--text menu-user">
           <v-card-title primary-title>
            <div>
              <div class="headline">your username </div>
              <span class="grey--text">username@gmail.com</span>
            </div>
          </v-card-title>
          <v-card-actions class="text-xs-center">
              <v-menu offset-y>
                <v-btn primary dark slot="activator">user menu</v-btn>
                <v-list>
                  <v-list-tile v-for="item in itemsMenu" :key="item.title">
                    <v-list-tile-title>{{ item.title }}</v-list-tile-title>
                  </v-list-tile>
                </v-list>
              </v-menu>
           
          </v-card-actions>
        </v-card>
      </v-flex>
      <v-list>
        <v-list-tile
          value="true"
          v-for="(item, i) in items"
          :key="i"
        >
          <v-list-tile-content>
            <v-list-tile-title v-text="item.title"></v-list-tile-title>
          </v-list-tile-content>
        </v-list-tile>
      </v-list>
    </v-navigation-drawer>
    <v-toolbar fixed>
      <v-toolbar-side-icon @click.stop="drawer = !drawer" light></v-toolbar-side-icon>
      <v-toolbar-title v-text="title"></v-toolbar-title>
      <v-spacer></v-spacer>
    </v-toolbar>
    <main>
      <v-container>
        <v-slide-y-transition mode="out-in">
          <v-layout column align-center>
            <v-data-table
              v-bind:headers="headers"
              v-bind:items="itemsTable"
              v-bind:search="search"
              v-model="selected"
              selected-key="name"
              select-all
              class="elevation-2"
            >
              <template slot="headerCell" scope="props">
                <span v-tooltip:bottom="{ 'html': props.header.text }">
                  {{ props.header.text }}
                </span>
              </template>
              <template slot="items" scope="props">
                <td>
                  <v-checkbox
                    primary
                    hide-details
                    v-model="props.selected"
                  ></v-checkbox>
                </td>
                <td>{{ props.item.name }}</td>
                <td class="text-xs-left">{{ props.item.lastName }}</td>
                <td class="text-xs-left">{{ props.item.email }}</td>
                <td class="text-xs-left">{{ props.item.role }}</td>
                <td class="text-xs-left">{{ props.item.signin }}</td>
                <td class="text-xs-left">{{ props.item.created }}</td>
              </template>
            </v-data-table>

          </v-layout>
        </v-slide-y-transition>
      </v-container>
      
    </main>
  </v-app>
</template>

<script>
  export default {
    data() {
      return {
        clipped: false,
        drawer: true,
        fixed: false,
        items: [
          { icon: 'bubble_chart', title: 'Dashboard' },
          { icon: 'bubble_chart', title: 'Leads' },
          { icon: 'bubble_chart', title: 'Flows' },
          { icon: 'bubble_chart', title: 'Forms' },
          { icon: 'bubble_chart', title: 'Page templates' },
          { icon: 'bubble_chart', title: 'Sms templates' },
          { icon: 'bubble_chart', title: 'Sms logs' },
          { icon: 'bubble_chart', title: 'Templates' },
          { icon: 'bubble_chart', title: 'Users' },
          { icon: 'bubble_chart', title: 'Roles' },
        ],
        itemsMenu: [
          { icon: 'bubble_chart', title: 'Profile' },
          { icon: 'bubble_chart', title: 'Option' },
          { icon: 'bubble_chart', title: 'Sign out' },

        ],
        miniVariant: false,
        right: true,
        rightDrawer: false,
        title: 'Test Masstraffic',
        selected: [],
        headers: [
          {
            text: 'First name',
            align: 'left',
            value: 'name',
          },
          { text: 'Last name', align: 'left', value: 'lastName' },
          { text: 'Email', align: 'left', value: 'email' },
          { text: 'Role', align: 'left', value: 'role' },
          { text: 'Last signin', align: 'left', value: 'signin' },
          { text: 'Created', align: 'left', value: 'created' },
        ],
        itemsTable: [
          {
            value: false,
            name: 'Vasja1',
            lastName: 'Test',
            email: 'useremail@gmail.com',
            role: 'super admin',
            signin: '01/01/2017',
            created: '01/01/2017',
          },
          {
            value: false,
            name: 'Ivan',
            lastName: 'Test',
            email: 'superuser@gmail.com',
            role: 'admin',
            signin: '01/08/2017',
            created: '01/08/2017',
          },
          {
            value: false,
            name: 'Ivan2',
            lastName: 'Test',
            email: 'superuser@gmail.com',
            role: 'admin',
            signin: '01/08/2017',
            created: '01/08/2017',
          },
          {
            value: false,
            name: 'Vasja3',
            lastName: 'Test',
            email: 'useremail@gmail.com',
            role: 'super admin',
            signin: '01/01/2017',
            created: '01/01/2017',
          },
          {
            value: false,
            name: 'Ivan4',
            lastName: 'Test',
            email: 'superuser@gmail.com',
            role: 'admin',
            signin: '01/08/2017',
            created: '01/08/2017',
          },
          {
            value: false,
            name: 'Ivan5',
            lastName: 'Test',
            email: 'superuser@gmail.com',
            role: 'admin',
            signin: '01/08/2017',
            created: '01/08/2017',
          },
          {
            value: false,
            name: 'Vasja6',
            lastName: 'Test',
            email: 'useremail@gmail.com',
            role: 'super admin',
            signin: '01/01/2017',
            created: '01/01/2017',
          },
          {
            value: false,
            name: 'Ivan7',
            lastName: 'Test',
            email: 'superuser@gmail.com',
            role: 'admin',
            signin: '01/08/2017',
            created: '01/08/2017',
          },
          {
            value: false,
            name: 'Ivan8',
            lastName: 'Test',
            email: 'superuser@gmail.com',
            role: 'admin',
            signin: '01/08/2017',
            created: '01/08/2017',
          },
          {
            value: false,
            name: 'Ivan9',
            lastName: 'Test',
            email: 'superuser@gmail.com',
            role: 'admin',
            signin: '01/08/2017',
            created: '01/08/2017',
          },
          {
            value: false,
            name: 'Ivan00',
            lastName: 'Test',
            email: 'superuser@gmail.com',
            role: 'admin',
            signin: '01/08/2017',
            created: '01/08/2017',
          },
        ],
      };
    },
  };
</script>

<style lang="stylus">
  @import './stylus/main'

  .menu-user {
    min-height: 170px;
  }

  .fab-position {
    position: absolute !important;
    right: 25px;
    bottom: 25px;
  }
</style>

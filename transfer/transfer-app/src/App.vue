<template>
  <div class="app">
    <div class="transfer-app">
        <ContactList 
        v-bind:contacts='contacts'
        @search-contact="searchContact"
        />
        <Wallet 
            :id="searched.id"
            :name='searched.name'
            :limit="searched.limit"
            @latest-params="latestParams"
        />
    </div>
  </div>
</template>

<script>
import ContactList from "./ContactList.vue";
import Wallet from "./Wallet.vue";

    export default {
    name: "app",
    data() {
        return {
            contacts: [
                { id: 1, name: "Emin", limit: 200 },
                { id: 2, name: "Ruslan", limit: 200 },
                { id: 3, name: "Samir", limit: 200 },
                { id: 4, name: "Ilkin", limit: 200 },
                { id: 5, name: "Murad", limit: 200 },
                { id: 6, name: "Valeh", limit: 200 },
                { id: 7, name: "Orxan", limit: 200 },
                { id: 8, name: "Elshad", limit: 200 },
                { id: 9, name: "Tural", limit: 200 },
                { id: 10, name: "Arif", limit: 200 }
            ],
            searched: {},
        };
    },
    methods: {
        searchContact(id) {
            this.searched = this.contacts.find(a => a.id === id)
        },

        latestParams(id, name, limit) {
            let x = this.contacts.find(a => a.id == id);
            x.limit = limit
        }
    },
    components: {
    ContactList,
    Wallet
}
};
</script>

<style>
@font-face {
  font-family: "Regular";
  src: url(./fonts/Montserrat-Regular.ttf)
}
@font-face {
  font-family: "Bold";
  src: url(./fonts/Montserrat-Bold.ttf)
}
@font-face {
  font-family: "Thin";
  src: url(./fonts/Montserrat-Thin.ttf)
}
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  list-style: none;
  text-decoration: none;
  font-family: "Regular";
}
.app {
  width: 100%;
  height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  background-color: #0069c3;
}
.transfer-app {
  width: 1100px;
  height: 600px;
  border: 2px solid whitesmoke;
  background-color: whitesmoke;
  box-shadow: 0px 0px 10px 2px rgb(71, 71, 71);
  border-radius: 10px;
  padding: 15px;
  display: flex;
  justify-content: space-between;
}
::selection {
    background-color: transparent;
}
</style>

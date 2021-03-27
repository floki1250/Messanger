<template>
  <q-layout view="hHh lpR fFf" class="hide-scrollbar">
    <q-drawer
      show-if-above
      v-model="left"
      side="left"
      class="drawer"
      id="drawer"
      content-class="bg-primary text-black"
      width="20%"
    >
      <q-toolbar>
        <q-btn round color="blue" flat @click="opensite">
          <q-avatar>
            <img
              src="https://scontent.ftun3-1.fna.fbcdn.net/v/t1.0-1/c22.0.197.197a/p240x240/141918388_4878713642204120_677171260476107958_n.jpg?_nc_cat=100&ccb=1-3&_nc_sid=7206a8&_nc_ohc=7AriXHSofqMAX8h-y-U&_nc_ht=scontent.ftun3-1.fna&tp=27&oh=69056beaf3b71ce90906cccc23fd35fb&oe=607624EB"
            />
          </q-avatar>
        </q-btn>
        <q-toolbar-title class="align-center">Messanger</q-toolbar-title>
        <q-btn round color="secondary" flat>
          <i class="fas fa-bars"></i>
        </q-btn>
      </q-toolbar>
      <q-separator />

      <div id="searchg" class="row">
        <transition name="slide-fade">
          <div
            v-show="active"
            class="col-12 col-md-8"
            @mouseleave="mouseOver"
            id="input-s"
          >
            <q-list>
              <input type="search" placeholder="Search" class="input-search" />
              <q-btn
                round
                flat
                color="red"
                size="10px"
                id="cancel-btn"
                icon="cancel"
              >
              </q-btn>
            </q-list>
          </div>
        </transition>
        <div
          @click="mouseOver"
          @mouseleave="!mouseOver"
          class="col-12 col-md-4"
          v-show="!active"
          id="search-icon"
        >
          <q-btn round color="secondary" flat size="20px">
            <i class="fas fa-search"></i>
          </q-btn>
        </div>
      </div>
      <q-separator />
      <div class="row">
        <div class="q-pa-md" id="Scroll">
          <q-scroll-area
            :thumb-style="thumbStyle"
            horizontal
            style="height: 70px; width: 320px;"
          >
            <div class="row no-wrap">
              <div v-for="n in 10" :key="n" class="q-pa-sm">
                <q-btn round color="secondary" flat size="9px">
                  <q-avatar color="secondary" text-color="white">A</q-avatar>
                </q-btn>
              </div>
            </div>
          </q-scroll-area>
        </div>

        <q-space></q-space>
        <div id="Scroll2">
          <q-scroll-area
            style="height: 380px; width: 100%;"
            :thumb-style="thumbStyle"
          >
            <div v-for="item of 10" :key="item">
              <q-card id="Scroll-i">
                <q-item clickable v-ripple>
                  <q-item-section avatar>
                    <q-avatar color="secondary" text-color="white">A</q-avatar>
                  </q-item-section>
                  <div>
                    <p class="name">I'm Beta</p>
                    <p>Hello ! I 💖 Messanger</p>
                  </div>
                </q-item>
              </q-card>
            </div>
          </q-scroll-area>
        </div>
      </div>
      <div class="Menu-footer">
        <button class="title" @click="showFb">
          <i class="fab fa-facebook"></i> My Profile
        </button>
        <div v-show="show_fb" style="width:100%; height:500px">
          <iframe
            id="myframe"
            src="https://www.facebook.com/"
            frameborder="0"
            style="width:100%; height:100%"
          ></iframe>
        </div>
      </div>
    </q-drawer>

    <q-page-container class="container" width="100%">
      <div class="titleChat">
        <q-avatar>
          <img src="../res/user.png" alt="" style="width:35px;height:35px;">
        </q-avatar>
        <div>
          <p class="user_chat">ChatBot 💬</p>
          <p class="active">active now  🟢</p>
        </div>
        <q-btn round icon="fas fa-phone-alt" padding="none" flat size="10px"></q-btn>
        <q-btn round icon="fas fa-video" padding="none" flat size="10px"></q-btn>
        <q-btn round icon="fas fa-search" padding="none" flat size="10px"></q-btn>
        <q-btn round icon="fas fa-ellipsis-v" padding="none" flat size="10px"></q-btn>
      </div>
      <div class="chat">
        <q-scroll-area style="height: 100%; width: 100%;">
          <div v-for="item of 5" :key="item">
            <q-chat-message
              name="me"
              avatar="https://cdn.quasar.dev/img/avatar1.jpg"
              :text="['hey, how are you?']"
              stamp="7 minutes ago"
              sent
              bg-color="amber-7"
            />
            <q-chat-message
              name="Jane"
              avatar="https://cdn.quasar.dev/img/avatar5.jpg"
              :text="['doing fine, how r you?']"
              stamp="4 minutes ago"
              text-color="white"
              bg-color="secondary"
            />
          </div>
        </q-scroll-area>
      </div>
      <div class="bottom-bar">
        <div><q-btn round padding="none" icon="fas fa-plus-circle" color="blue-10" /></div>
        
          <input type="search" placeholder="Type a message.."  class="input-msg"/>
        
        <div style="padding-left:20px">
          <q-btn round padding="none" icon="fas fa-smile" color="blue-10" />
        </div>
      </div>
    </q-page-container>
  </q-layout>
</template>

<script>
export default {
  name: "MainLayout",

  data() {
    return {
      left: false,
      active: false,
      show_fb: false,
      text: "",
      thumbStyle: {
        right: "2px",
        borderRadius: "5px",
        backgroundColor: "#F9A12EFF",
        width: "10px",
        opacity: 0.9
      }
    };
  },
  methods: {
    opensite: function() {
      window.open("https://facebook.com/adam1250/", "_blank");
    },
    mouseOver: function() {
      this.active = !this.active;
    },
    showFb: function() {
      this.show_fb = !this.show_fb;
    }
  }
};
</script>

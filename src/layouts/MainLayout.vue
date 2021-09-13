<template>
  <div class="q-pa-md">
    <q-layout view="hHh Lpr lff">
      <q-drawer
        v-model="drawer"
        show-if-above
        :mini="!drawer || miniState"
        @click.capture="drawerClick"
        :width="300"
        :breakpoint="500"
        class="bg-white"
      >
        <div class="row" style="padding: 10px 0px 0px 20px">
          <q-avatar size="40px">
            <img src="../assets/logo.svg" alt=""
          /></q-avatar>
          <p class="app-name">WeChat</p>
          <q-space />
          <div>
            <q-btn color="black-6" icon="las la-edit" flat round dense />
          </div>
          <div>
            <q-btn
              flat
              dense
              round
              unelevated
              color="black"
              icon="eva-menu-outline"
              @click="miniState = true"
            />
          </div>
        </div>
        <div class="userSection">
          <div style="padding: 20px 0px 0px 105px">
            <q-btn flat round
              ><q-avatar size="50px" color="indigo" text-color="white"
                >A
              </q-avatar></q-btn
            >
          </div>
          <div>
            <div
              class="row"
              style="margin: 10px 0px 0px 30%; width: 100%; height: 100%"
            >
              <p>Dardour Adem</p>
              <div>
                <q-btn color="black" flat icon="las la-cog" size="xs" round />
              </div>
            </div>
            <p
              class="text"
              style="margin: -10px 35% 0px 30%; width: 100%; height: 100%"
            >
              Web Developer
            </p>
            <ToggleActive
              v-model="active"
              @click="active = !active"
              style="margin: 0px 0px 0px 30%"
            />
          </div>
        </div>
        <template v-slot:mini>
          <div style="padding: 10px 0px 0px 10px">
            <q-avatar size="40px">
              <img src="../assets/logo.svg" alt=""
            /></q-avatar>
          </div>

          <div class="q-py-lg">
            <div class="column items-center">
              <div>
                <q-btn
                  flat
                  dense
                  round
                  unelevated
                  color="black"
                  icon="eva-menu-outline"
                  @click="miniState = true"
                />
              </div>
              <q-scroll-area
                class="mini-slot"
                style="width: 50px; height: 450px"
                :thumb-style="{ opacity: 0 }"
              >
                <q-list padding>
                  <div
                    class="row"
                    v-for="i in 50"
                    :key="i"
                    style="border-radius: 2px; padding: 5px"
                  >
                    <div class="item-rippel">
                      <q-avatar
                        size="40px"
                        font-size="20px"
                        color="blue-8"
                        text-color="white"
                        ><img :src="user.img[i]" alt=""
                      /></q-avatar>
                    </div>
                  </div>
                </q-list>
              </q-scroll-area>
            </div>
          </div>
        </template>
        <div class="row" style="margin-left: 20px">
          <p>Active Conversation</p>
          <div style="height: 100%">
            <q-badge
              rounded
              color="badgeColor"
              label="5"
              style="margin-left: 5px"
              text-color="txtcolor"
            />
          </div>

          <span
            style="
              position: relative;
              left: 90px;
              top: 0px;
              width: fit-content;
              height: fit-content;
            "
            @click="switchConversation"
          >
            <q-icon :name="ConvIcon" flat round size="15px" />
          </span>
        </div>
        <q-slide-transition>
          <div v-if="HideConversation" style="margin: 0px 20px 0px 20px">
            <q-scroll-area style="height: 45vh" :thumb-style="{ opacity: 0 }">
              <q-list padding>
                <q-item clickable v-ripple v-for="i in 5" :key="i">
                  <div class="row">
                    <div>
                      <q-avatar
                        size="40px"
                        font-size="20px"
                        color="teal"
                        text-color="white"
                        ><img :src="user.img[i]" alt=""
                      /></q-avatar>
                    </div>
                    <div>
                      <p style="margin: 10px">user {{ i }}</p>
                    </div>
                  </div>
                </q-item>
              </q-list>
            </q-scroll-area>
          </div>
        </q-slide-transition>
        <div class="row" style="margin-left: 20px">
          <p>Archived Conversations</p>
          <div>
            <q-badge
              rounded
              color="badgeColor"
              label="7"
              style="margin-left: 5px"
              text-color="txtcolor"
            />
          </div>
          <span
            style="
              position: relative;
              left: 67px;
              top: 0px;
              width: fit-content;
              height: fit-content;
            "
            @click="switchArchivedConv"
          >
            <q-icon :name="ConvIcon2" flat round size="15px" />
          </span>
        </div>
        <q-slide-transition>
          <div v-if="HideArchivedConv" style="margin: 0px 20px 0px 20px">
            <q-scroll-area style="height: 45vh" :thumb-style="{ opacity: 0 }">
              <q-list padding>
                <q-item clickable v-ripple v-for="i in 7" :key="i">
                  <div class="row">
                    <div>
                      <q-avatar
                        size="40px"
                        font-size="20px"
                        color="teal"
                        text-color="white"
                        ><img :src="user.img[i]" alt=""
                      /></q-avatar>
                    </div>
                    <div>
                      <p style="margin: 10px">User {{ i }}</p>
                    </div>
                  </div>
                </q-item>
              </q-list>
            </q-scroll-area>
          </div>
        </q-slide-transition>
      </q-drawer>

      <q-page-container style="width: 100%; height: 95vh" class="row">
        <div class="MessageSection">
          <q-infinite-scroll
            reverse
            style="width: 100%; height: 85vh; overflow: scroll; margin: 5px"
            ref="infiniteScroll"
          >
            <div
              class="caption q-py-sm"
              style="width: 100%; padding: 10px"
              v-if="messageCounter > 1"
            >
              <q-chat-message
                avatar="https://cdn.quasar.dev/img/avatar5.jpg"
                :text="[
                  'doing fine, how r you?',
                  'I just feel like typing a really, really, REALLY long message to annoy you...',
                ]"
                size="6"
                stamp="4 minutes ago"
              />

              <q-chat-message
                v-for="messageCounter in messagesCount"
                v-bind:key="messageCounter"
                avatar="https://cdn.quasar.dev/img/avatar3.jpg"
                stamp="7 minutes ago"
                sent
                >{{ messageContent[messageCounter] }}</q-chat-message
              >
              <div
                v-if="messageOnfocus == true"
                style="position: relative; left: 90%"
              >
                <q-spinner-comment color="blue-10" size="2em" />
              </div>
              <div
                style="width: 59px; height: 100px; background: #f2f6fc"
              ></div>
            </div>
          </q-infinite-scroll>

          <div class="inputmessage row">
            <q-file
              v-model="files"
              label="Standard"
              outlined
              multiple
              dense
              v-show="false"
              ref="fileUploader"
              @update:model-value="filesCounter"
            />
            <div style="flex: 4">
              <q-input
                v-model="message"
                type="text"
                placeholder="Enter your Message Here"
                dense
                outlined
                rounded
                color="blue-9"
                @focus="messageOnfocus = true"
                @blur="messageOnfocus = false"
                style="max-height: 10px"
              >
                <template v-slot:default>
                  <q-chip
                    removable
                    color="primary"
                    text-color="white"
                    icon="las la-file"
                    v-if="filesCount > 0"
                    @remove="(files = null), (filesCount = 0)"
                    @mouseenter="viewfiles = true"
                    >{{ filesCount }} files</q-chip
                  >
                  <div
                    class="fileUpload"
                    v-if="viewfiles"
                    @mouseleave="
                      () => {
                        viewfiles = false;
                      }
                    "
                  >
                    <q-scroll-area style="width: 200px; height: 80px">
                      <div v-for="(file, i) in files" :key="file" class="row">
                        <q-chip
                          removable
                          color="primary"
                          text-color="white"
                          icon="las la-file"
                          @remove="files.splice(i, 1), filesCount--"
                          >{{
                            file.name.substring(0, 10).concat("...")
                          }}</q-chip
                        >
                      </div>
                    </q-scroll-area>
                  </div>
                </template>

                <template v-slot:before>
                  <q-btn
                    color="primary"
                    icon="las la-paperclip"
                    flat
                    round
                    @click="fileUpload"
                  >
                  </q-btn>
                </template>
                <template v-slot:append
                  ><q-btn
                    color="orange"
                    icon="las la-smile"
                    flat
                    round
                    @click="showEmoji = true"
                  >
                  </q-btn
                ></template>
              </q-input>
            </div>

            <div style="flex: 0.5; position: relative; right: -3%">
              <q-btn
                color="blue-7"
                icon="eva-paper-plane-outline"
                size="md"
                @click="sendMessage"
                flat
              >
              </q-btn>
            </div>
          </div>
        </div>
        <div class="user column">
          <div class="user-info-1">
            <q-avatar size="60px" color="blue-5" text-color="white">A</q-avatar>
            <p style="color: gray">User name</p>
            <q-btn
              color="blue"
              icon-right="eva-archive-outline"
              label="Archive"
              @click="onClick"
              outline
              rounded
            />
          </div>
          <div class="user-info-2">
            <p style="margin: 10px; color: gray">Shared Files</p>
            <q-scroll-area style="width: 100%; height: 200px">
              <div class="row wrap">
                <div v-for="i in Sentfiles" :key="i">
                  <div @click="openurl(i.url)">
                    <q-chip color="black-6">
                      <div v-if="loading == true">
                        {{ fileUploadValue.toFixed(2) }} %
                      </div>
                      <div v-else>
                        {{
                          i.name.length > 8
                            ? i.name.slice(0, 5).concat("...")
                            : i.name
                        }}
                      </div>
                    </q-chip>
                  </div>
                </div>
              </div>
            </q-scroll-area>
          </div>
          <div class="user-info-3"></div>
        </div>
        <transition
          appear
          enter-active-class="animated fadeIn"
          leave-active-class="animated fadeOut"
        >
          <Emoji
            @inssmile="insertSmileys"
            v-if="showEmoji == true"
            @mouseleave="showEmoji = false"
            style="position: absolute; top: 50%; left: 50%; z-index: 9000"
          />
        </transition>
      </q-page-container>
    </q-layout>
  </div>
</template>
<script>
import { ref as Vueref } from "vue";
import ToggleActive from "src/components/Toggle-Active.vue";
import { api } from "boot/axios";
import Emoji from "src/components/Emoji.vue";
import { initializeApp } from "firebase/app";
import {
  getStorage,
  ref,
  uploadBytesResumable,
  getDownloadURL,
} from "firebase/storage";

initializeApp({});

var uploadTask;
export default {
  components: { ToggleActive, Emoji },
  mounted() {
    // Initialize Firebase
  },
  data() {
    return {
      loading: false,
      fileUploadValue: null,

      index: 0,
      Sentfiles: [
        {
          name: "",
          url: null,
        },
      ],
      sendMessageClicked: false,
      filesCount: 0,
      files: null,
      viewfiles: false,
      showEmoji: false,
      messageOnfocus: false,
      messageContent: [""],
      messagesCount: 0,
      messageCounter: 1,
      message: "",
      ConvIcon: "eva-arrow-ios-upward-outline",
      ConvIcon2: "eva-arrow-ios-downward-outline",
      toggle: true,
      HideConversation: true,
      active: true,
      HideArchivedConv: false,
      user: {
        name: [],
        img: [],
      },
    };
  },
  methods: {
    sendMessage() {
      var scroll = 0;
      var filename = "";
      //this.index = filesOnserver.lenght+1
      var sendMessage = new Promise(() => {
        this.loading = true;
        if (this.files != null) {
          //--------------------
          for (var i = 0; i < this.files.length; i++) {
            //filename = this.files[i].name;
            try {
              const storage = getStorage();
              var storageRef = ref(storage, this.files[i].name);
              // 'file' comes from the Blob or File API
              uploadTask = uploadBytesResumable(storageRef, this.files[i]);

              uploadTask.catch((e) => {
                console.log(e);
              });
              uploadTask.on("state_changed", (snapshot) => {
                this.fileUploadValue =
                  (snapshot.bytesTransferred / snapshot.totalBytes) * 100;
                console.log(this.fileUploadValue);
              });
              uploadTask.then((snapshot) => {
                getDownloadURL(ref(storageRef)).then((url) => {
                  this.Sentfiles[this.index] = Object.assign(
                    {},
                    this.Sentfiles[this.index],
                    {
                      name: this.files[this.index].name,
                      url: url,
                    }
                  );

                  console.log(i, this.index, url);
                  this.index++;
                });
                this.loading = false;
                //this.FirebaseUrl = "Empty";
              });
            } catch (error) {
              console.log(error);
            }
          }

          // this.filesCount = 0;
        }
        if (this.message != "") {
          this.messageContent[this.messageCounter] = this.message;
          this.messageCounter++;
          this.messagesCount++;
          this.message = "";
          const el = document.querySelector(".q-infinite-scroll");
          // get scroll position in px
          scroll = el.scrollTop + 500;
          el.scrollTop = scroll;
        }
      });
      sendMessage.finally(() => {
        console.log("send message fianlly");
      });
      sendMessage.then(() => {
        console.log("send message then");
        this.files = null;
      });
    },
    openurl(url) {
      window.open(url).focus();
      console.log(url);
    },
    filesCounter() {
      this.filesCount = this.files.length;
    },
    fileUpload() {
      this.$refs.fileUploader.$el.click();
    },
    insertSmileys: function (value) {
      this.message += value;
    },

    switchArchivedConv() {
      this.HideArchivedConv = !this.HideArchivedConv;
      if (this.HideArchivedConv == false) {
        this.ConvIcon2 = "eva-arrow-ios-downward-outline";
      } else {
        this.HideConversation = false;
        this.ConvIcon = "eva-arrow-ios-downward-outline";
        this.ConvIcon2 = "eva-arrow-ios-upward-outline";
      }
    },
    switchConversation() {
      this.HideConversation = !this.HideConversation;
      if (this.HideConversation == false) {
        this.ConvIcon = "eva-arrow-ios-downward-outline";
      } else {
        this.HideArchivedConv = false;
        this.ConvIcon2 = "eva-arrow-ios-downward-outline";
        this.ConvIcon = "eva-arrow-ios-upward-outline";
      }
    },
  },
  mounted() {
    api
      .get("")
      .then((response) => {
        for (let i = 0; i < response.data.length; i++) {
          this.user.name[i] = response.data[i].id;
          this.user.img[i] = response.data[i].urls[3]["256"];
        }
      })
      .catch((e) => {
        console.log(e);
      });
  },
  setup() {
    const miniState = Vueref(true);
    return {
      drawer: Vueref(false),
      miniState,
      drawerClick(e) {
        if (miniState.value) {
          miniState.value = false;
          e.stopPropagation();
        }
      },
      onLoad(index, done) {
        setTimeout(() => {
          index++;
          done;
        }, 2000);
      },
    };
  },
};
</script>

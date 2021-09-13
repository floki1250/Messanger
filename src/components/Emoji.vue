<template>
  <q-card style="width: 300px">
    <q-splitter v-model="splitterModel" style="height: 200px">
      <template v-slot:before>
        <q-tabs v-model="tab" vertical class="text-blue-8">
          <q-tab name="Smileys" icon="las la-grin-alt" />
          <q-tab name="Gestures" icon="las la-hand-peace" />
          <q-tab name="Animals" icon="las la-dog" />
          <q-tab name="Food" icon="las la-hamburger" />
        </q-tabs>
      </template>

      <template v-slot:after>
        <q-tab-panels
          v-model="tab"
          animated
          swipeable
          vertical
          transition-prev="jump-up"
          transition-next="jump-up"
        >
          <q-tab-panel name="Smileys">
            <div class="text-h4 q-mb-xs">Smileys</div>
            <q-scroll-area style="width: 200px; height: 150px">
              <div class="row no-wrap">
                <div class="q-gutter-sm">
                  <q-btn
                    round
                    flat
                    v-for="i in emojiList.smiles"
                    :key="i"
                    v-model="selected"
                    @click="insertSmileys"
                    @mouseenter="selected = i"
                    size="md"
                  >
                    {{ i }}
                  </q-btn>
                </div>
              </div>
            </q-scroll-area>
          </q-tab-panel>
          <q-tab-panel name="Gestures">
            <div class="text-h4 q-mb-xs">Gestures</div>
            <q-scroll-area style="width: 200px; height: 150px">
              <div class="row no-wrap">
                <div class="q-gutter-sm">
                  <q-btn
                    round
                    flat
                    v-for="i in emojiList.Gestures"
                    :key="i"
                    v-model="selected"
                    @click="insertSmileys"
                    @mouseenter="selected = i"
                    size="md"
                  >
                    {{ i }}
                  </q-btn>
                </div>
              </div>
            </q-scroll-area>
          </q-tab-panel>
          <q-tab-panel name="Animals">
            <div class="text-h4 q-mb-xs">Animals</div>
            <q-scroll-area style="width: 200px; height: 150px">
              <div class="row no-wrap">
                <div class="q-gutter-sm">
                  <q-btn
                    round
                    flat
                    v-for="i in emojiList.Animals"
                    :key="i"
                    v-model="selected"
                    @click="insertSmileys"
                    @mouseenter="selected = i"
                    size="md"
                  >
                    {{ i }}
                  </q-btn>
                </div>
              </div>
            </q-scroll-area>
          </q-tab-panel>
          <q-tab-panel name="Food">
            <div class="text-h4 q-mb-xs">Food</div>
            <q-scroll-area style="width: 200px; height: 150px">
              <div class="row no-wrap">
                <div class="q-gutter-sm">
                  <q-btn
                    round
                    flat
                    v-for="i in emojiList.Food"
                    :key="i"
                    v-model="selected"
                    @click="insertSmileys"
                    @mouseenter="selected = i"
                    size="md"
                  >
                    {{ i }}
                  </q-btn>
                </div>
              </div>
            </q-scroll-area>
          </q-tab-panel>
        </q-tab-panels>
      </template>
    </q-splitter>
  </q-card>
</template>
<script>
import { ref } from "vue";
export default {
  name: "Emoji",

  data() {
    return {
      selected: "",
      emojiCount: 0,
      emojiList: {
        smiles: [
          "😀",
          "😃",
          "😄",
          "😁",
          "😆",
          "😅",
          "😂",
          "🤣",
          "😊",
          "😇",
          "🙂",
          "🙃",
          "😉",
          "😌",
          "😍",
          "🥰",
          "😘",
          "😗",
          "😙",
          "😚",
          "😋",
          "😛",
          "😝",
          "😜",
          "🤪",
          "🤨",
          "🧐",
          "🤓",
          "😎",
          "🤩",
          "🥳",
          "😏",
          "😒",
          "😞",
          "😔",
          "😟",
          "😕",
          "🙁",
          "☹️",
          "😣",
          "😖",
          "😫",
          "😩",
          "🥺",
          "😢",
          "😭",
          "😤",
          "😠",
          "😡",
          "🤬",
          "🤯",
          "😳",
          "🥵",
          "🥶",
          "😱",
          "😨",
          "😰",
          "😥",
          "😓",
          "🤗",
          "🤔",
          "🤭",
          "🤫",
          "🤥",
          "😶",
          "😐",
          "😑",
          "😬",
          "🙄",
          "😯",
          "😦",
          "😧",
          "😮",
          "😲",
          "🥱",
          "😴",
          "🤤",
          "😪",
          "😵",
          "🤐",
          "🥴",
          "🤢",
          "🤮",
          "🤧",
          "😷",
          "🤒",
          "🤕",
          "🤑",
          "🤠",
          "😈",
          "👿",
          "👹",
          "👺",
          "🤡",
          "💩",
          "👻",
          "💀",
          "☠️",
          "👽",
          "👾",
          "🤖",
          "🎃",
          "😺",
          "😸",
          "😹",
          "😻",
          "😼",
          "😽",
          "🙀",
          "😿",
          "😾",
          "❤️",
          "🧡",
          "💛",
          "💚",
          "💙",
          "💜",
          "🖤",
          "🤍",
          "🤎",
          "💔",
          "❣️",
          "💕",
          "💞",
          "💓",
          "💗",
          "💖",
          "💘",
          "💝",
        ],
        Food: [
          "🍏",
          "🍎",
          "🍐",
          "🍊",
          "🍋",
          "🍌",
          "🍉",
          "🍇",
          "🍓",
          "🍈",
          "🍒",
          "🍑",
          "🥭",
          "🍍",
          "🥥",
          "🥝",
          "🍅",
          "🍆",
          "🥑",
          "🥦",
          "🥬",
          "🥒",
          "🌶",
          "🌽",
          "🥕",
          "🧄",
          "🧅",
          "🥔",
          "🍠",
          "🥐",
          "🥯",
          "🍞",
          "🥖",
          "🥨",
          "🧀",
          "🥚",
          "🍳",
          "🧈",
          "🥞",
          "🧇",
          "🥓",
          "🥩",
          "🍗",
          "🍖",
          "🦴",
          "🌭",
          "🍔",
          "🍟",
          "🍕",
          "🥪",
          "🥙",
          "🧆",
          "🌮",
          "🌯",
          "🥗",
          "🥘",
          "🥫",
          "🍝",
          "🍜",
          "🍲",
          "🍛",
          "🍣",
          "🍱",
          "🥟",
          "🦪",
          "🍤",
          "🍙",
          "🍚",
          "🍘",
          "🍥",
          "🥠",
          "🥮",
          "🍢",
          "🍡",
          "🍧",
          "🍨",
          "🍦",
          "🥧",
          "🧁",
          "🍰",
          "🎂",
          "🍮",
          "🍭",
          "🍬",
          "🍫",
          "🍿",
          "🍩",
          "🍪",
          "🌰",
          "🥜",
          "🍯",
          "🥛",
          "🍼",
          "☕️",
          "🍵",
          "🧃",
          "🥤",
          "🍶",
          "🍺",
          "🍻",
          "🥂",
          "🍷",
          "🥃",
          "🍸",
          "🍹",
          "🧉",
          "🍾",
          "🧊",
          "🥄",
          "🍴",
          "🍽",
          "🥣",
          "🥡",
          "🥢",
          "🧂",
        ],
        Animals: [
          "🐶",
          "🐱",
          "🐭",
          "🐹",
          "🐰",
          "🦊",
          "🐻",
          "🐼",
          "🐻‍❄️",
          "🐨",
          "🐯",
          "🦁",
          "🐮",
          "🐷",
          "🐽",
          "🐸",
          "🐵",
          "🙈",
          "🙉",
          "🙊",
          "🐒",
          "🐔",
          "🐧",
          "🐦",
          "🐤",
          "🐣",
          "🐥",
          "🦆",
          "🦅",
          "🦉",
          "🦇",
          "🐺",
          "🐗",
          "🐴",
          "🦄",
          "🐝",
          "🐛",
          "🦋",
          "🐌",
          "🐞",
          "🐜",
          "🦟",
          "🦗",
          "🕷",
          "🕸",
          "🦂",
          "🐢",
          "🐍",
          "🦎",
          "🦖",
          "🦕",
          "🐙",
          "🦑",
          "🦐",
          "🦞",
          "🦀",
          "🐡",
          "🐠",
          "🐟",
          "🐬",
          "🐳",
          "🐋",
          "🦈",
          "🐊",
          "🐅",
          "🐆",
          "🦓",
          "🦍",
          "🦧",
          "🐘",
          "🦛",
          "🦏",
          "🐪",
          "🐫",
          "🦒",
          "🦘",
          "🐃",
          "🐂",
          "🐄",
          "🐎",
          "🐖",
          "🐏",
          "🐑",
          "🦙",
          "🐐",
          "🦌",
          "🐕",
          "🐩",
          "🦮",
          "🐕‍🦺",
          "🐈",
          "🐈‍⬛",
          "🐓",
          "🦃",
          "🦚",
          "🦜",
          "🦢",
          "🦩",
          "🕊",
          "🐇",
          "🦝",
          "🦨",
          "🦡",
          "🦦",
          "🦥",
          "🐁",
          "🐀",
          "🐿",
          "🦔",
          "🐾",
          "🐉",
          "🐲",
          "🌵",
          "🎄",
          "🌲",
          "🌳",
          "🌴",
          "🌱",
          "🌿",
          "☘️",
          "🍀",
          "🎍",
          "🎋",
          "🍃",
          "🍂",
          "🍁",
          "🍄",
          "🐚",
          "🪨",
          "🌾",
          "💐",
          "🌷",
          "🌹",
          "🥀",
          "🌺",
          "🌸",
          "🌼",
          "🌻",
          "🌞",
          "🌝",
          "🌛",
          "🌜",
          "🌚",
          "🌕",
          "🌖",
          "🌗",
          "🌘",
          "🌑",
          "🌒",
          "🌓",
          "🌔",
          "🌙",
          "🌎",
          "🌍",
          "🌏",
          "🪐",
          "💫",
          "⭐️",
          "🌟",
          "✨",
          "⚡️",
          "☄️",
          "💥",
          "🔥",
          "🌪",
          "🌈",
          "☀️",
          "🌤",
          "⛅️",
          "🌥",
          "☁️",
          "🌦",
          "🌧",
          "⛈",
          "🌩",
          "🌨",
          "❄️",
          "☃️",
          "⛄️",
          "🌬",
          "💨",
          "💧",
          "💦",
          "☔️",
          "☂️",
          "🌊",
          "🌫",
        ],
        Gestures: [
          "👋",
          "🤚",
          "🖐",
          "✋",
          "🖖",
          "👌",
          "🤏",
          "✌️",
          "🤞",
          "🤟",
          "🤘",
          "🤙",
          "👈",
          "👉",
          "👆",
          "🖕",
          "👇",
          "☝️",
          "👍",
          "👎",
          "✊",
          "👊",
          "🤛",
          "🤜",
          "👏",
          "🙌",
          "👐",
          "🤲",
          "🤝",
          "🙏",
          "✍️",
          "💅",
          "🤳",
          "💪",
          "🦾",
          "🦵",
          "🦿",
          "🦶",
          "👣",
          "👂",
          "🦻",
          "👃",
          "🧠",
          "🦷",
          "🦴",
          "👀",
          "👁",
          "👅",
          "👄",
          "💋",
          "🩸",
        ],
      },
      emoji: "",
      tab: ref("Smileys"),
      splitterModel: ref(20),
    };
  },
  methods: {
    insertSmileys: function (value) {
      this.$emit("inssmile", this.selected);
    },
  },
};
</script>
<style lang="scss">
@import url("https://fonts.googleapis.com/css2?family=Righteous&family=Rubik:wght@300&display=swap");
.text {
  text-transform: capitalize;
  font-family: "Rubik", sans-serif;
  font-weight: 600;
  padding-left: 10px;
  font-size: 13px;
  color: #6b7783;
}
</style>

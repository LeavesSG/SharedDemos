<template>
  <div class="document-body">
    <h1>Tianyi Liu Oct 25 2021</h1>
    <section class="section-hci">
      <h1>What is Good Code?</h1>
      <div class="showcase">
        <div class="HCI-string">
          <span>HCI, the abbreviations of &nbsp;</span>
          <transition-group name="switch-group">
            <span
              class="switch-group-item"
              v-for="(item, key) in HCIString"
              :key="getKey(item, key)"
            >
              {{ item }}
            </span>
          </transition-group>
        </div>
        <div class="button" @click="switchAcitvedString">Switch</div>
      </div>
      <p>
        The 5 Characteristics of Usable Products In 2001, Whitney Quesenbery,
        the UX and Usability Expert and former President of the Usability
        Professionals’ Association (UXPA), offered five criteria that a product
        must meet to be usable:
      </p>
      <span @mouseover="showHint[0] = 1"
        >1. Effectiveness<span class="hint" v-if="showHint[0] === 1"
          >你这代码保熟嘛?</span
        ></span
      >
      <span @mouseover="showHint[1] = 1"
        >2. Efficiency<span class="hint" v-if="showHint[1] === 1"
          >好跑吗?</span
        ></span
      >
      <span @mouseover="showHint[2] = 1"
        >3. Engagingness<span class="hint" v-if="showHint[2] === 1"
          >酷不酷,想不想学?</span
        ></span
      >
      <span @mouseover="showHint[3] = 1"
        >4. Error Tolerance<span
          class="hint"
          id="hint4"
          v-if="showHint[3] === 1"
          >----------------------------------><img
            src="../assets/error.png" /></span
      ></span>
      <span @mouseover="showHint[4] = 1"
        >5. Ease of Learning<span class="hint" v-if="showHint[4] === 1"
          >你看看这说的是人话吗?</span
        ></span
      >
    </section>
    <section class="section-css">
      <h1>Transition Group</h1>
      <p>
        different way to bind keys:
        <span @click="bindKeyTypeShowList = true" class="check-out-btn">{{
          `check it out >>`
        }}</span>
      </p>
      <div class="bind-key-switch" v-if="bindKeyTypeShowList">
        <span
          class="bind-key-switch-item"
          :class="{ active: bindKeyType === item }"
          v-for="(item, key) in bindKeyTypeList"
          :key="key"
          @click="bindKeyType = item"
          >{{ item }}</span
        >
      </div>
      <a
        href="https://v3.cn.vuejs.org/guide/transitions-list.html#%E5%88%97%E8%A1%A8%E7%9A%84%E7%A7%BB%E5%8A%A8%E8%BF%87%E6%B8%A1"
        >Vue3 Document of Transition Group</a
      >
    </section>

    <section class="section-ghpages">
      <h1>Github Pages</h1>
      <p>A simple and reliable place to host your blog / portfolio!</p>
    </section>
  </div>
</template>

<style scoped>
.document-body {
  width: 60%;
  background: #eeeeff;
  margin: auto;
  text-align: left;
  padding-left: 1%;
}
.section-hci {
  display: flex;
  flex-direction: column;
}
.showcase {
  display: flex;
  align-items: center;
}
.HCI-string {
  border: 1px solid #00000080;
  border-left: 5px solid #00d6f9;
  width: 50%;
  height: 50px;
  font-size: 1em;
  line-height: 50px;
  padding-left: 2em;
}
.switch-group-item {
  transition: all 0.55s ease;
  display: inline-block;
  font-style: italic;
}

.switch-group-enter-from,
.switch-group-leave-to {
  opacity: 0;
  transform: translateY(30px);
}

.switch-group-leave-active {
  position: absolute;
}

.switch-group-move {
  transition: all 0.55s cubic-bezier(0.075, 0.82, 0.165, 1);
}

.button {
  width: 80px;
  height: 40px;
  border: 1px solid #00000080;
  display: flex;
  align-items: center;
  justify-content: center;
  margin-left: 2%;
  cursor: pointer;
  transition: all 0.35s ease-in;
}
.button:hover {
  color: #eeeeee;
  background: #444444;
  transition: all 0.35s ease-out;
}
.button:active {
  background: #000000;
}
.bind-key-switch {
  display: flex;
  gap: 1%;
  margin-bottom: 1%;
}
.bind-key-switch-item {
  box-sizing: border-box;
  border: 1px solid #00d6f980;
  padding: 0.3%;
  cursor: pointer;
  transition: all 0.2s ease-in;
}
.bind-key-switch-item:hover {
  box-shadow: 0 1px 8px #00d6f9;
  border: 1px solid #00d6f980;
  transition: all 0.2s ease-out;
}
.bind-key-switch-item.active {
  background: #0080a0;
  color: white;
  transition: all 0.2s ease-out;
}
.check-out-btn {
  margin-left: 2%;
  cursor: pointer;
}
.hint {
  margin-left: 5%;
}
#hint4 img {
  position: absolute;
  left: 37%;
  border: 1px dashed black;
}
</style>
<script>
export default {
  data() {
    return {
      HCIString1: "Human-Computer-Interaction",
      HCIString2: "Human-Code-Interaction",
      activedStringIndex: 1,
      bindKeyType: "key",
      bindKeyTypeList: ["key", "item", "item+key", "key+random"],
      bindKeyTypeShowList: false,
      showHint: [0, 0, 0, 0, 0],
    };
  },
  computed: {
    HCIString() {
      return this.activedStringIndex === 1
        ? this.HCIString1.split("")
        : this.HCIString2.split("");
    },
  },
  methods: {
    switchAcitvedString() {
      if (this.activedStringIndex === 1) {
        this.activedStringIndex = 2;
        return;
      }
      this.activedStringIndex = 1;
    },
    getKey(item, key) {
      switch (this.bindKeyType) {
        case "key":
          return key;
        case "item":
          return item;
        case "item+key":
          return item + key;
        case "key+random":
          return key + Math.random();
        default:
          return key;
      }
    },
  },
};
</script>
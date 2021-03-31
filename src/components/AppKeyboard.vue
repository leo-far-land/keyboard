<template>
  <div v-on="event()">
    <span v-for="(key, i) in set" :key="key" >
      <b-button squared variant="outline-primary" :class="{back: key === '⇦', tab: key === 'tab', caps: key === 'caps', enter: key === 'enter', shift: key === 'shift', space: key === 'space'}" @click="getClick(key)">
        {{key}} 
      </b-button>
      <div v-if="i === 13 || i === 27 || i === 40 || i === 52"></div>
    </span>
  </div>
</template>

<script>
export default {
  data() {
    return {
      text: "",
      shift: false,
      caps: false,
      set: [
        "`", "1", "2", "3", "4", "5", "6", "7", "8", "9", "0", "-", "=", "⇦",
        "tab", "q", "w", "e", "r", "t", "y", "u", "i", "o", "p", "[", "]", "\\",
        "caps", "a", "s", "d", "f", "g", "h", "j", "k", "l", ";", "'", "enter",
        "shift", "z", "x", "c", "v", "b", "n", "m", ",", ".", "/", "shift", 
        "space"
      ],
      standardKeyList: [
        "`", "1", "2", "3", "4", "5", "6", "7", "8", "9", "0", "-", "=", "⇦",
        "tab", "q", "w", "e", "r", "t", "y", "u", "i", "o", "p", "[", "]", "\\",
        "caps", "a", "s", "d", "f", "g", "h", "j", "k", "l", ";", "'", "enter",
        "shift", "z", "x", "c", "v", "b", "n", "m", ",", ".", "/", "shift", 
        "space"
      ],
      shiftKeyList: [
        "~", "!", "@", "#", "$", "%", "^", "&", "*", "(", ")", "_", "+", "⇦",
				"tab", "Q", "W", "E", "R", "T", "Y", "U", "I", "O", "P", "{", "}", "|",
				"caps", "A", "S", "D", "F", "G", "H", "J", "K", "L", ":", '"', "enter",
				"shift", "Z", "X", "C", "V", "B", "N", "M", "<", ">", "?", "shift", 
				"space"
      ],
      capsKeyList: [
        "`", "1", "2", "3", "4", "5", "6", "7", "8", "9", "0", "-", "=", "⇦",
				"tab", "Q", "W", "E", "R", "T", "Y", "U", "I", "O", "P", "[", "]", "\\",
				"caps", "A", "S", "D", "F", "G", "H", "J", "K", "L", ";", "'", "enter",
				"shift", "Z", "X", "C", "V", "B", "N", "M", ",", ".", "/", "shift", 
				"space"
      ],
    }
  },
  methods: {
    getClick(key) {
      switch(key) {
        case "⇦":
          this.text = this.text.substr(0, this.text.length - 1);
          break;
        case "tab":
          this.text += '\t';
          break;
        case "caps":
          this.caps = !this.caps;
          this.set = this.caps ? this.capsKeyList : this.standardKeyList;
          break;
        case "enter":
          this.text += '\n';     
          break;
        case "shift":
          this.shift = !this.shift;
          this.set = this.shift ? this.shiftKeyList : this.standardKeyList;
          break;
        case "space":
          this.text += ' ';
          break;
        default:
          this.text += key.toString();
          break;
      }
    },
    event() {
      this.$emit("text", this.text);
    },
  }
}
</script>

<style>
* {
  font-size: 10pt;
}

button {
  height: 35px;
  width: 35px;
}

.tab, .back {
  color: pink;
  width: 60px;
}

.caps {
  width: 50px;
}

.enter {
  width: 80px;
}

.shift {
  width: 83px;
}

.space {
  width: 210px;
}
</style>
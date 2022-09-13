<script>
import { defineComponent } from "vue";
import ZombieCharComponent from "@/zombie-char-component.vue";

export default defineComponent({
  name: "ServeDev",
  components: {
    ZombieCharComponent,
  },
  data() {
    return {
      // dna: "010101010101",
      name_list: ["A", "B", "C", "D", "E", "F", "G", "H", "I", "J"],
      name:"zombie",
      shirt: 1
    };
  },
});
</script>

<template>
  <div id="app">
    <!-- <input v-model = "dna" /> -->
    <input v-model = "name" />
    <!-- <zombie-char-component :isZombieLoaded="false" /> -->

    <!-- <zombie-char-component
      :isZombieLoaded="true"
      zombieName="Zombie1"
      :autoGenerate="false"
      :eyeChoice="5"
      :clothesColorChoice="50"
    /> -->
    
    <br/><br/><br/>
    <zombie-char-component
      :isZombieLoaded="true"
      :optionalDna=null
      :zombieName="name"
      :autoGenerate="true"
    />
    <br/><br/><br/>
    <ul>
    <li v-for="index in 10" :key="index">
      <zombie-char-component
      :isZombieLoaded="true"
      :optionalDna=null
      :zombieName="name_list[index]"
      :autoGenerate="true"
    />
    </li>
    </ul>

    <!-- <zombie-char-component
      :isZombieLoaded="true"
      :optionalDna="dna"
      :zombieName="name"
      :autoGenerate="true"
      :catMode="false"
    /> -->
    
    <!-- <zombie-char-component
      :isZombieLoaded="true"
      :zombieName="name"
      :autoGenerate="true"
    /> -->
  </div>
</template>

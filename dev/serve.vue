<script>
import { defineComponent } from "vue";
import ZombieCharComponent from "@/zombie-char-component.vue";
import scroll from "@/assets/scroll_arrow.png";

export default defineComponent({
  name: "ServeDev",
  components: {
    ZombieCharComponent,
  },
  data() {
    return {
      // dna: "010101010101",
      name_list: JSON.parse(localStorage.getItem('names')),
      // len : this.name_list.length,
      stored_list: [],
      name:"zombie",
      size: JSON.parse(localStorage.getItem('list_size')),
      // size:10,
      submit_bool: false,
      scrollImage: scroll,
    };
  },
  methods: {
    addNewName() {
      this.name_list.push(this.name);
      this.size = this.size + 1;
      this.submit_bool = true;
      localStorage.setItem('names', JSON.stringify(this.name_list));
      localStorage.setItem('list_size', this.size)
      console.log(this.name_list);
    }
  },
});
</script>

<template>
  <!-- <h1 class="heading">Create Your Zombie</h1> -->
  <div id="app" class="contain">
    <!-- <h1>Create Your Zombie</h1> -->

    <!-- <input v-model = "dna" /> -->
    
    <!-- <zombie-char-component :isZombieLoaded="false" /> -->

    <!-- <zombie-char-component
      :isZombieLoaded="true"
      zombieName="Zombie1"
      :autoGenerate="false"
      :eyeChoice="5"
      :clothesColorChoice="50"
    /> -->
    <h1 class="header">ZOMBIE GENERATOR</h1>
    <br/>


    <div class="containers">
      <div class="container-1">
        

        <br/><br/>

        <div class="card" style="width: 15rem;">
          
          <zombie-char-component class="card-img-top"
            :isZombieLoaded="true"
            :optionalDna=null
            :zombieName="name"
            :autoGenerate="true"
          />
        </div>

        <br/>
        <!-- <br/> -->
        <!-- <br/> -->
        
        <input v-model = "name" />
        <button style="margin:10px;" type="button" class="btn btn-secondary" v-on:click="addNewName">Submit</button>

        <!-- <form v-on:submit.prevent="addNewName">
        <input v-model="name" />
        <button style="margin:10px;" type="button" class="btn btn-secondary">Submit</button>
        </form> -->
        <br/>
        <!-- <br/> -->
        <!-- <img class="arrow" src="../src/assets/scroll_arrow.png" style="max-width: 70px; max-height:auto;"/> -->
      </div>

      <!-- <zombie-char-component
        :isZombieLoaded="true"
        :optionalDna=null
        :zombieName="name"
        :autoGenerate="true"
      /> -->
      
      <br/>
      <ul class="container-2">
      <li v-for="index in size" :key="index" class="container-2-">
        <div class="card" style="width: 15rem;">
          
          <zombie-char-component class="card-img-top"
            :isZombieLoaded="true"
            :optionalDna=null
            :zombieName="name_list[size - index]"
            :autoGenerate="true"
          />
          <div class="card-body" style = "height: 3rem;">
            <h5 class="card-title">{{name_list[size - index]}}</h5>
            <!-- <p class="card-text">Some quick example text to build on the card title and make up the bulk of the card's content.</p> -->
          </div>
        </div>
        
    
      </li>
      </ul>
    </div>
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


<style>

  template {
    background-color: #000000;
  }

  .contain {
    display: flex;
    flex-direction: column;
    min-width: 100%;
    background-color: rgb(42, 54, 54);
  }

  .header {
    color: rgb(16, 181, 223);
    text-align: center;
    margin-top: 20px;
    font-size: 60px;
    font-family: 'Courier New', Courier, monospace;
    font-weight: bold;
  }

  .containers {
    display: flex;
    flex-direction: row;
    /* width: 100%; */
    /* background-color: rgb(42, 54, 54); */
  }

  .container-1 {
    /* width: 30%; */
    margin: 80px;
    height: 100%;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
  }

  .arrow {
            /* width:100%; */
            /* height:100%; */
            object-fit: cover;
            animation: float 3s ease-out infinite;
  }

  @keyframes float {
      50% {
      transform: translate(0, 30px);
      }
  }

  .container-2 {
    /* width: auto; */
    list-style: none;
    display: flex;
    flex-direction: column;
    flex-flow: row wrap;
    margin: 20px;
    align-items: center;
    justify-content: center;
    /* padding: 5px; */
  }

  .container-2- {
    /* background-color: aquamarine; */
    margin: 5px;
  }

  h1 {
    align-items: center;
    background-color: rgb(42, 54, 54);
    color: white;
  }

  .card-img-top {
    width: 100%;
    height: 15rem;
    object-fit: cover;
  }

</style>
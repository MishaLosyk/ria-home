<template>
  <div>
    <Error 
    v-bind:nameIsError='nameIsError'
    v-bind:emailIsError='emailIsError'
    v-bind:ageIsError='ageIsError'
    v-bind:isValidForm='isValidForm'
    />
    <form @submit.prevent="add"> 
      <div class="row g-3">
        <div class="col-sm-5">
          <input type="text" class="form-control" v-model="name" placeholder="Your Name">
        </div>
        <div class="col-sm-5">
          <input type="text" class="form-control" v-model="email" placeholder="Your Email">
        </div>
        <div class="col-sm">
          <input type="number" class="form-control" v-model="age" placeholder="Your Age">
        </div>
      </div>
      <br>
      <div class="col">
        <button type="submit" v-bind:disabled="isValidForm" class="btn btn-primary">Add User</button>
      </div>

    </form>
  </div>

</template>

<script>
import Error from "@/components/Error";
export default {
  name: "AddUser",
  components: {Error},

  data () {
    return {
      name: '',
      email: '',
      age: null,
      nameIsError: Boolean,
      emailIsError: Boolean,
      ageIsError: Boolean,
    }
  },

  methods: {
    add: function() {
       this.$emit('add', {name: this.name, email: this.email, age: this.age}); 
    }
  },

  watch: {

    name: function(val){
      if(!val || val < 2 ||val > 20){
        this.nameIsError = true;
      } else {this.nameIsError = false}
    },
    
    email: function(val){
      let regexp = /.+@.+\...+/i;
      this.emailIsError = !regexp.test(val);
    },
    
    age: function(val){
      if(!val || val < 1) {
        this.ageIsError = true
      } else {
        this.ageIsError = false
      }
      if(val.toString().length > 2) {
        this.age = Number.parseInt(val.toString().slice(0,2));
      }
    },


  },

  computed: {
       isValidForm: function(){
         return (this.nameIsError || this.emailIsError || this.ageIsError);
        
      },
  }

}
</script>

<style scoped>

</style>
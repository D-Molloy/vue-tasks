<template>
  <div class="hello">
    <div class="holder">
      <form @submit.prevent="addSkill">

       <input type="text" placeholder="Enter a task..." v-model="task" v-validate="'min:5'" name="skill">
     
      <transition name="alert-in" enter-active-class="animated flipInX" leave-active-class="animated flipOutX">
       <p class="alert" v-if="errors.has('skill')">{{errors.first('skill')}}</p>
      </transition>
      </form>
      
      <ul>
        <transition-group name="list" enter-active-class="animated bounceInUp" leave-active-class="animated bounceOutDown">
          <li v-for="(data, index) in tasks" :key="index">
            {{data.task}}
            <i class="fa fa-minus-circle" v-on:click="remove(index)"></i>
            </li>
        </transition-group>
      </ul>
      <p v-if="tasks.length >= 1">You have {{tasks.length}} tasks to complete!  Get working.</p>
      <p v-else>You've finished all your tasks!  Time for more!</p>
      </div>
    </div>
  
</template>

<script>
export default {
  name: "Tasks",
  data() {
    return {
      task: "",
      tasks: [
        { task: "Do your taxes." },
        { task: "Work out for an hour." },
        { task: "Do laundry." }
      ]
    };
  },
  methods: {
    addSkill() {
      this.$validator.validateAll().then(result => {
        if (result) {
          this.tasks.push({ task: this.task });
          this.task = "";
        } else {
          console.log("Not valid");
        }
      });
    },
    remove(id){
      this.tasks.splice(id, 1)
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<!-- add a src="[location]" in the style tag to include external css -->
<style scoped>
/* import the animate css library */
@import "https://cdn.jsdelivr.net/npm/animate.css@3.5.1";
/* import font-awesome */
@import "https://maxcdn.bootstrapcdn.com/font-awesome/4.7.0/css/font-awesome.min.css"; 
.holder {
  background: #fff;
}

ul {
  margin: 0;
  padding: 0;
  list-style-type: none;
}

ul li {
  padding: 20px;
  font-size: 1.3em;
  background-color: #e0edf4;
  border-left: 5px solid #3eb3f6;
  margin-bottom: 2px;
  color: #3e5252;
}

p {
  padding-bottom: 20px;
  text-align: center;
  color: gray;
}

.container {
  box-shadow: 0px 0px 40px lightgray;
}

input {
  width: calc(100% - 40px);
  border: 0;
  padding: 20px;
  font-size: 1.3em;
  background-color: #323333;
  color: #687f7f;
}

.alert {
  background: #fdf2ce;
  font-weight: bold;
  display: inline-block;
  padding: 5px;
  margin-top: -20px;
}

.alert-in-enter-active {
  animation: bounce-in 0.5s;
}
.alert-in-leave-active {
  animation: bounce-in 0.5s reverse;
}

@keyframes bounce-in {
  0% {
    transform: scale(0);
  }
  50% {
    transform: scale(1.5);
  }
  100% {
    transform: scale(1);
  }
}

i{
  float: right;
  cursor: pointer;
}
</style>

<template>
  <div class="hello">
    <div class="holder">
      <p v-if="tasks.length > 1">You have {{tasks.length}} tasks to complete!  Get working.</p>
      <p v-else>You've finished all your tasks!  Time for more!</p>
      <ul>
        <li v-for="(data, index) in tasks" :key="index">{{data.task}}</li>
      </ul>
      
      <p>Hear are your tasks for the day.</p>
      </div>
    </div>
  
</template>

<script>
export default {
  name: "Tasks",
  data() {
    return {
      tasks: [
        { task: "Do your taxes." },
        { task: "Work out for an hour." },
        { task: "Do laundry." }
      ],
      bgColor: "blue",
      bgWidth: "70%",
      bgHeight: "10%"
    };
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<!-- add a src="[location]" in the style tag to include external css -->

<style scoped>
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
  text-align: center;
  padding: 30px 0;
  color: gray;
}

.container {
  box-shadow: 0px 0px 40px lightgray;
}
</style>

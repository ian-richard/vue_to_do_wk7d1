<template>
 <div id="app">
   <h1> ToDo list </h1>
   <form v-on:submit.prevent="saveNewItem">
     
     <input id="new-item" type="text" v-model="newItem"/>
     <!-- radio buttons -->
     <label for="High">High</label>
     <input type="radio" id="high" value="High" v-model="picked">
     <label for="Low">Low</label>
     <input type="radio" id="low" value="Low" v-model="picked">
     
     <!-- end-radios -->
     <input type="submit" value="Save item">
   </form>

   <ul>
     <li v-for="(item, index) in items" :key="index"
     v-bind:class="item.isCompleted ? 'completed':'not-completed'">
     <span>{{item.name}}</span>
     <span v-if="item.isCompleted">Completed!</span>
     <button v-if="!item.isCompleted" v-on:click="completeItem(index)">Complete</button>
     </li>
   </ul>
 </div>
</template>

<script>
export default {
  data(){
    return {
      items: [
        {name: "Buy shopping", isCompleted: false},
        {name: "Clean bathroom", isCompleted: true},
        {name: "Car's MOT", isCompleted: false}
      ],
      newItem: ""
    }
  },
  methods: {
    saveNewItem: function(){
      this.items.push({
        name: this.newItem,
        isCompleted: false
      });
      this.newItem = "";
    },
    completeItem: function(index){
      this.items[index].isCompleted = true;
    }
}
}
</script>

<style>
#app {
  width: 60%;
  margin: 0 auto;
  font-family: 'Lato', sans-serif;
}

ul {
  margin: 0;
  padding: 0;
  list-style-type: none;
}

li {
  margin: 20px 0;
  padding: 10px;
  display: flex;
  justify-content: space-between;
}

li span {
  padding: 8px;
}

li button {
  background: black;
  color: #fff;
  border: none;
  padding: 10px;
  cursor: pointer;
}

li.completed {
  border: 2px solid #1a681e;
  color: #1a681e;
}

li.not-completed {
  border: 2px solid red;
}

input[type="text"] {
  padding: 10px;
  width: 50%;
  margin:5px;
}

button, input[type="submit"]{
  padding: 10px;
  background: #000;
  color: #fff;
  cursor: pointer;
  border: 1px solid #000;
}

</style>
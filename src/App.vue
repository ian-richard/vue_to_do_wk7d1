<template>
 <div id="app">
   <h1> ToDo's </h1>
   <form v-on:submit.prevent="saveNewItem">
     
     <input id="new-item" type="text" v-model="newItem"/>
     <!-- radio buttons -->
     <label for="High">High</label>
     <input type="radio" id="priority" name="priority" v-model="pick" v-bind:value="true">
     <label for="Low">Low</label>
     <input type="radio" id="priority" name="priority" v-model="pick" v-bind:value="false">
     
     <!-- end-radios -->
     <input type="submit" value="Save item">
   </form>

   <ul>
     <li v-for="(item, index) in items" :key="index"
     v-bind:class="item.priority ? 'priority':'no-priority'">
     <span>{{item.name}}</span>
     <!-- <span v-if="item.priority"></span> -->
     <!-- <button v-if="!item.isPriority" v-on:click="completeItem(index)">Complete</button> -->
     </li>
   </ul>
 </div>
</template>

<script>
export default {
  data(){
    return {
      items: [
        {name: "Buy shopping", priority: false},
        {name: "Clean bathroom", priority: true},
        {name: "Car's MOT", priority: false}
      ],
      newItem: ""
    }
  },
  methods: {
    saveNewItem: function(){
      this.items.push({
        name: this.newItem,
        priority: this.pick
      });
      this.newItem = "";
    },
    // completeItem: function(index){
    //   this.items[index].isPriority = true;
    // }
}
}
</script>

<style>
#app {
  width: 45%;
  margin: 0 auto;
  font-family: Arial, Helvetica, sans-serif
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

/* li button {
  background: black;
  color: #fff;
  border: none;
  padding: 10px;
  cursor: pointer;
} */

li.priority {
  border: 2px solid red;
  color: red;
}

li.no-priority {
  border: 2px solid black;
  color: black;
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
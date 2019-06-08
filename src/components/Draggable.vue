<template>
  <div class="hello">
    <h1>Group Selector</h1>
    <main class="parent">
      <div v-for="(group, index) in groups" class="{`div${group}`} each" :key="`group-${index}`">
        <h4>{{groups.indexOf(group) + 1}}</h4>
        <ul>
          <draggable class="list-group" :list="group" group="people">
            <li v-for="(person, index) in group" :key="`person-${index}`">{{person}}</li>
          </draggable>
        </ul>
      </div>

      <div class="unselected">
        <h4>Unselected</h4>
        <p>Names, separated by commas</p>
        <form action="GET">
          <input type="text" v-model="namesInput">
          <button type="submit" @click.prevent="addToUnselected">Add names</button>
        </form>
        <ul>
          <draggable class="list-group" :list="dataUnselected" group="people">
            <li v-for="(person, index) in dataUnselected" :key="`person-${index}`">{{person}}</li>
          </draggable>
        </ul>
      </div>
    </main>
  </div>
</template>

<script>
import draggable from 'vuedraggable';
export default {
  name: 'Draggable',
  components: {
    draggable,
  },
  props: {
    msg: String,
  },
  data: () => {
    return {
      namesInput: '',
      dataUnselected: [],
      groups: (() => {
        let arr = [];
        for (let i = 0; i < 12; i++) {
          arr.push([]);
        }
        return arr;
      })(),
    };
  },
  methods: {
    addToUnselected: function() {
      const newNames = this.namesInput.split(',').map(name => name.trim());
      this.dataUnselected = this.dataUnselected.concat(newNames);
      this.namesInput = '';
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
li {
  border: 1px solid black;
  margin: 2px;
}
ul {
  padding-top: 1em;
  padding-bottom: 1em;
  border: 1px solid blue;
  list-style-position: inside;
}
div {
  margin: 0.1em;
}
.parent {
  display: grid;

  grid-template-columns: 1fr 1fr 1fr 1fr;

  grid-template-rows: 1fr 1fr 1fr 1fr;

  grid-column-gap: 0px;

  grid-row-gap: 0px;
  border: 1px solid chartreuse;
}
.div0 {
  grid-area: 1 / 1 / 2 / 2;
}

.div1 {
  grid-area: 2 / 1 / 3 / 2;
}

.div2 {
  grid-area: 3 / 1 / 4 / 2;
}

.div3 {
  grid-area: 4 / 1 / 5 / 2;
}

.div4 {
  grid-area: 1 / 2 / 2 / 3;
}

.div5 {
  grid-area: 2 / 2 / 3 / 3;
}

.div6 {
  grid-area: 3 / 2 / 4 / 3;
}

.div7 {
  grid-area: 4 / 2 / 5 / 3;
}

.div8 {
  grid-area: 1 / 3 / 2 / 4;
}

.div9 {
  grid-area: 2 / 3 / 3 / 4;
}

.div10 {
  grid-area: 3 / 3 / 4 / 4;
}

.div11 {
  grid-area: 4 / 3 / 5 / 4;
}

.unselected {
  grid-area: 1 / 4 / 5 / 5;
}
</style>

<template>
  <div class="hello">
    <h1>Group Selector</h1>
    <main class="parent">
      <div v-for="group in groups" class="{`div${group}`} each" :key="`group-${group}`">
        <h4>{{group + 1}}</h4>
        <ul>
          <draggable class="list-group" :list="draggable" group="people">
            <li v-for="person in group0" :key="person">{{person}}</li>
          </draggable>
        </ul>
      </div>
      <!-- <div class="div1">
        <h4>1</h4>
        <ul>
          <draggable class="list-group" :list="draggable" group="people">
            <li v-for="person in group1" :key="person">{{person}}</li>
          </draggable>
        </ul>
      </div>-->
      <div class="unselected">
        <h4>Unselected</h4>
        <ul>
          <draggable class="list-group" :list="draggable" group="people">
            <li v-for="person in dataUnselected" :key="person">{{person}}</li>
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
      dataUnselected: [
        'Aaron',
        'Adam',
        'Andrew',
        'Aoki',
        'Christian',
        'Christina',
        'Daniel',
        'David',
        'Devin',
        'Edward',
        'Everett',
        'Felix',
        'Georgia',
        'Helan',
        'Heon',
        'Iman',
        'Jacob',
        'Jessica',
        'Joe',
        'Keil',
        'Kim',
        'Lawrence',
        'Maryanne',
        'Meghan',
        'Monali',
        'Monica',
        'Nina',
        'Scott',
        'Sophia',
        'Weiming',
      ],
      group0: [],
      group1: [],
      groups: (() => {
        let arr = [];
        for (let i = 0; i < 12; i++) {
          arr.push(i);
        }
        return arr;
      })(),
    };
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

<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <main class="parent">
      <div class="div0">Hi</div>
      <div class="div1">Hi1</div>
      <div class="unselected">
        <h4>Unselected</h4>
        <ul>
          <li v-for="person in dataUnselected" :key="person">{{person}}</li>
        </ul>
      </div>
    </main>
  </div>
</template>

<script>
import draggable from 'vuedraggable';
export default {
  name: 'Draggable',
  props: {
    msg: String,
  },
  data: () => {
    return {
      dataUnselected: ['Keil', 'Jacob', 'Sophia', 'Meghan', 'Arron'],
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
div {
  border: 1px solid salmon;
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

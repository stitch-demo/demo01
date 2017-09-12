<template>
  <div class="hello">
    <h1>Demo</h1>
    <div v-for="(q, index) in questions" :key="index" v-if="q.seq <= current">
      <h3>{{ q.text }}</h3>
      <h4 v-if="isSelected(q.seq)">a</h4>
      <ul v-else>
        <li v-for="(c, i2) in q.choices" :key="i2">
          <button @click="selectChoice(q.seq, c)">{{ c }}</button>
        </li>
      </ul>
      <br/>
      <br/>
    </div>
  </div>
</template>

<script>
export default {
  name: 'demo',
  data () {
    return {
      current: 1,
      selected: [],
      questions: [
        {
          seq: 1,
          text: 'Question One',
          choices: [
            'One A', 'One B', 'One C', 'One D'
          ]
        },
        {
          seq: 2,
          text: 'Question Two',
          choices: [
            'Two A', 'Two B', 'Two C', 'Two D'
          ]
        },
        {
          seq: 3,
          text: 'Question Three',
          choices: [
            'Three A', 'Three B', 'Three C', 'Three D'
          ]
        },
        {
          seq: 4,
          text: 'Question Four',
          choices: [
            'Four A', 'Four B', 'Four C', 'Four D'
          ]
        }
      ]
    }
  },

  methods: {
    addSeq () {
      this.current = this.current + 1
    },
    isSelected (seq) {
      return this.getSelected(seq) !== null
    },
    getSelected (seq) {
      let selected = this.selected.filter(i => i.seq === seq)
      if (selected.length > 0) {
        return selected[0]
      } else {
        return null
      }
    },
    selectChoice (seq, text) {
      this.selected.push({ seq, text })
      this.addSeq()
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1,
h2 {
  font-weight: normal;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}
</style>

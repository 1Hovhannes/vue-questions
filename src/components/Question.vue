<template>
  <div class="alert">
    <!-- <h3>{{ x }} + {{ y }} = {{answer}}</h3> -->
    <h3>{{ x }} + {{ y }} = ?</h3>
    <hr />
    <div class="buttons">
      <button
        class="btn"
        v-for="number in answers"
        v-bind:key="number"
        v-on:click="onAnswer(number)"
      >
        {{ number }}
      </button>

      <!--//////////////////////////////
         <button class="btn">
        {{ answers }}
      </button>
      ////////////////////////////////// -->
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      x: mtRand(100, 200),
      y: mtRand(100, 200)
    };
  },
  computed: {
    good() {
      return this.x + this.y;
    },
    answers() {
      /////////////////////////////////
      // return this.x + this.y;
      /////////////////////////////////
      // let good = this.x + this.y;//
      let math = [this.good];

      while (math.length < 4) {
        let num = mtRand(this.good - 20, this.good + 20);

        if (math.indexOf(num) === -1) {
          math.push(num);
        }
      }
      return math.sort(function() {
        return Math.random() > 0.5;
      });
    }
  },
  methods: {
    onAnswer(num) {
      // console.log(num);
      if (num == this.good) {
        // console.log(1);
        this.$emit('success');
      } else {
        // console.log(0);
        this.$emit('error', `${this.x} + ${this.y} = ${this.good}!`);
      }
    }
  }
};

function mtRand(min, max) {
  let diff = max - min;
  return Math.floor(Math.random() * diff) + min;
}
</script>

<style scoped>
.alert {
  padding: 20px 0;
  background: #eee;
}

h3 {
  display: flex;
  justify-content: center;
}

.buttons {
  display: flex;
  justify-content: space-around;
}

.btn {
  background-color: green;
  color: white;
}
</style>

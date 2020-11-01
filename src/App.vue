<template>
  <div class="trining">
    <h1>Math trining</h1>
    <hr />
    <appStartScreen v-if="state == 'start'" v-on:onStart="onStart" />
    <appQuestion
      v-else-if="state == 'question'"
      v-on:success="onQuestSuccess"
      v-on:error="onQuestError"
    />
    <appMessage
      v-else-if="state == 'message'"
      v-bind:type="message.type"
      v-bind:text="message.text"
      v-on:onNext="onNext"
    />
    <appResultScreen v-else-if="state == 'results'" />
    <div v-else>Unknown state</div>
  </div>
</template>

<script>
import appStartScreen from './components/StartScreen.vue';
import appQuestion from './components/Question.vue';
import appMessage from './components/Message.vue';
import appResultScreen from './components/ResultScreen.vue';

export default {
  name: 'App',
  data() {
    return {
      state: 'start',
      stats: {
        success: 0,
        error: 0
      },
      message: {
        type: '',
        text: ''
      }
    };
  },
  computeed: {
    questDone() {
      return this.stats.success + this.stats.error;
    }
  },
  methods: {
    onStart() {
      this.state = 'question';
    },
    onQuestSuccess() {
      this.state = 'message';
      this.message.text = 'Good Job';
      this.message.type = 'success';
    },
    onQuestError(msg) {
      this.state = 'message';
      this.message.text = msg;
      this.message.type = 'error';
    },
    onNext() {
      this.state = 'question';
    }
  },
  components: {
    appStartScreen,
    appQuestion,
    appMessage,
    appResultScreen
  }
};
</script>

<style>
.trining {
  max-width: 700px;
  margin: 20px auto;
}
</style>

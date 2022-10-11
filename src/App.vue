<script setup>
import EmojiInput from '@/components/EmojiInput.vue'
import { ref } from 'vue'
const emoji = ref('')
const submit = () => {
  console.log('Emoji: ', emoji.value)
}
</script>
<template>
  <div id="app" class="row d-flex justify-content-center">
    <div class="col-md-5 mt-3">
      <div class="card">
        <div class="card-header">Emoji Selector</div>
        <div class="card-body">
          <form @submit.prevent="submit">
            <div class="mb-2">
              <EmojiInput v-model="emoji" :options="{ position: 'bottom' }" />
            </div>
            <button type="submit" class="btn btn-primary">Submit</button>
          </form>
        </div>
      </div>
    </div>
  </div>
  <h2 v-if="emoji">
    The emoji name is <span>"{{ emoji.name }}"</span>
  </h2>
</template>

<style src="bootstrap/dist/css/bootstrap.css"></style>
<style scoped lang="scss">
h2 {
  margin-top: 1rem;
  font-size: 1.5em;
  text-align: center;
  span {
    color: #f35626;
    -webkit-animation: hue 60s infinite linear;
    animation: hue 60s infinite linear;
  }
}
@keyframes hue {
  from {
    -webkit-filter: hue-rotate(0deg);
  }

  to {
    -webkit-filter: hue-rotate(360deg);
  }
}
</style>

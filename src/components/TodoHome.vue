<template>
  <v-container fluid>
    <v-form>
        <v-file-input
          label="Selecione as Legendas"
          prepend-icon="mdi-message-text"
          append-outer-icon="mdi-send"
          outlined
          multiple 
          chips 
          v-model="files" 
          @click:append-outer="processSubtitles"/>

    </v-form>
    <div class="pills">
        <TodoPill v-for="word in groupedWords" :key="word.name" 
            :name="word.name" :amount="word.amount" />
    </div>
  </v-container>
</template>

<script>
import { ipcRenderer } from 'electron'
import TodoPill from './TodoPill.vue'

export default {
  components: { TodoPill },
  data: function () {
    return {
        files: [],
        groupedWords: [
          { name: 'i', amount: 1234 }, 
          { name: 'you', amount: 900 },
          { name: 'he', amount: 853 },
        ]
    }
  },
  methods: {
    processSubtitles() {
        console.log(this.files)

        ipcRenderer.send('blabla', 'ping')
        ipcRenderer.on('blabla', (event, resp) => {
          console.log(resp)
        })
    }
  }

}
</script>

<style>
  .pills {
    display: flex;
    flex-wrap: wrap;
    justify-content: space-between;
}
</style>
<script>
import CharacterStatistics from './components/CharacterStatistics.vue';
export default {
  components: {
    CharacterStatistics
  },
  data: () => ({
    newCharacter: {
      name: '',
      status: [],
    },
    characterList: [
      {
        name: 'Catherine de Medici',
        status: ['Royalty'],
      },
      {
        name: 'Rahima',
        status: ['Servant'],
      },
      {
        name: 'Anjou',
        status: ['Royalty'],
      },
      {
        name: 'Antoine de Borboun',
        status: ['Royalty'],
      },
    ],
    favoriteList: [],
  }),
  methods: {
    favoriteCharacter(character) {
      this.favoriteList.push(character)
    },
    addNewCharacter() {
      this.characterList.push(this.newCharacter)
      this.newCharacter = { name: '' }
    },
  },
}
</script>

<template>
  <div id="app">
    <CharacterStatistics: characters="characterList" />
    <h2>Characters</h2>
    <p v-if="characterList.length === 0">There are no characters</p>
    <ul v-else-if="characterList.length % 2 === 0">
      <li v-for="(character, index) in characterList" :key="`even-character-${index}`">
        <p>{{ character.name }}</p>
        <button @click="favoriteCharacter(character)">⭐ Favorite</button>
      </li>
    </ul>
    <p v-else>There are odd characters!</p>

    <h2>Favorite Characters</h2>
    <ul v-if="favoriteList.length > 0">
      <li v-for="(character, index) in favoriteList" key="`odd-character-${index}`">
        {{ character }}
      </li>
    </ul>
    <p v-else>No favorite characters yet!</p>

    <h2>New Character</h2>
    <p>
      {{ newCharacter }}
    </p>
    <label for="character-name">Name</label>
    <input type="text" v-model="newCharacter.name" @keyup.enter="addNewCharacter" />

    <p>
      <span v-for="(character, index) in characterList" key="`comma-list-character-${index}`">
        {{ character.name }}{{ index === characterList.length - 1 ? '' : ', ' }}
      </span>
    </p>
  </div>
</template>

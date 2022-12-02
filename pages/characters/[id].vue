<script setup lang="ts">
const route = useRoute()
type Character = {
  character: {
    name: string
    id: string
    image: string
    status: string
    species: string
    location: {
      name: string
    }
  }
}

const query = gql`
  query getCharacter {
    character(id: ${route.params.id}) {
        name
        image
        status
        id
        species
        gender
        location {
          name
        }
      }
    }
`

const { data } = await useAsyncQuery<Character>(query)
</script>

<template>
  <div class="bg-white">
    <a class="" href="/"
      ><div class="flex space-x-2 justify-center mt-3">
        <button
          type="button"
          class="inline-block px-6 py-2.5 bg-blue-600 text-white font-medium text-xs leading-tight uppercase rounded shadow-md hover:bg-blue-700 hover:shadow-lg focus:bg-blue-700 focus:shadow-lg focus:outline-none focus:ring-0 active:bg-blue-800 active:shadow-lg transition duration-150 ease-in-out"
        >
          Go Back
        </button>
      </div></a
    >

    <div class="mx-auto max-w-2xl py-16 px-4 sm:py-24 sm:px-6 lg:max-w-7xl lg:px-8">
      <h2 class="sr-only">Rick and Morty Characters</h2>

      <div
        class="grid grid-cols-1 gap-y-10 gap-x-6 sm:grid-cols-2 lg:grid-cols-3 xl:grid-cols-4 xl:gap-x-8"
      >
        <CharacterCard
          :id="data.character.id"
          :name="data.character.name"
          :image="data.character.image"
          :status="data.character.status"
          :species="data.character.species"
          :location="data.character.location.name"
        />
      </div>
    </div>
  </div>
</template>

<template>
  <div>
    <HeaderHero />
    <div class="bg-white">
      <div class="mx-auto max-w-2xl py-16 px-4 sm:py-24 sm:px-6 lg:max-w-7xl lg:px-8">
        <h2 class="sr-only">Rick and Morty Characters</h2>

        <div
          class="grid grid-cols-1 gap-y-10 gap-x-6 sm:grid-cols-2 lg:grid-cols-3 xl:grid-cols-4 xl:gap-x-8"
        >
          <CharacterCard
            v-for="{ id, name, image, status, species, location } in data.characters
              .results"
            :key="id"
            :id="id"
            :name="name"
            :image="image"
            :status="status"
            :species="species"
            :location="location.name"
          />
        </div>
      </div>
    </div>
  </div>
</template>

<script lang="ts" setup>
type CharacterResults = {
  characters: {
    results: {
      id: string
      name: string
      image: string
      status: string
      species: string
      location: {
        name: string
      }
    }[]
  }
}
const query = gql`
  query getCharacters {
    characters {
      results {
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
  }
`

const { data } = await useAsyncQuery<CharacterResults>(query)
</script>

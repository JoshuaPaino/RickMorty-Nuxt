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
  <CharacterCard
    :id="data.character.id"
    :name="data.character.name"
    :image="data.character.image"
    :status="data.character.status"
    :species="data.character.species"
    :location="data.character.location.name"
  />
</template>

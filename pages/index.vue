<template>
  <v-row justify="center" align="center">
    <v-col cols="12" sm="8" md="6">
      <v-card class="logo py-4 d-flex justify-center">
        <NuxtLogo />
        <VuetifyLogo />
      </v-card>
      <v-card>
        <ul v-for="mountain in mountains" :key="mountain.id">
        <NuxtLink :to="`${mountain.continent.toLowerCase()}/${mountain.slug}`">
        <li>{{ mountain.title }}</li>
        </NuxtLink>
        </ul>
      </v-card>
      <v-card>
        <NuxtLink :to="`GOTOSLUG`">
        <li>SLUG DEFAULT</li>
        </NuxtLink>
      </v-card>
      <v-card>
        <NuxtLink :to="`/parent`">
        <li>PARENT ROUTE</li>
        </NuxtLink>
      </v-card>
    </v-col>
  </v-row>
</template>

<script>
export default {
  async asyncData() {
    const mountains = await fetch(
      'https://api.nuxtjs.dev/mountains'
    ).then((res) => res.json())

    return { mountains }
  }
}
</script>

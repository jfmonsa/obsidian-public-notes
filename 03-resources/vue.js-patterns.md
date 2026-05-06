---
mocs:
    - "[[vue.js]]"
tags:
  - programming_patterns
start_date: 2026-04-14 07:28
links:
---
# Container Presentational Component
+ Classification between "Dumb" (presentational / stateless) and "Smart" (container) components 
+ Main goal of the container component is to **pass data** to presentational components
+ container component doesn't usually have styling
```vue.js
<!-- DogImagesContainer.vue -->

<template>
  <DogImages :dogs="dogs" />
</template>

<script setup>
  import { ref, onMounted } from "vue";
  import DogImages from "./DogImages.vue";

  const dogs = ref([]);

  onMounted(async () => {
    const response = await fetch(
      "https://dog.ceo/api/breed/labrador/images/random/6"
    );
    const { message } = await response.json();
    dogs.value = message;
  });
</script>
```
+ this pattern can be replaced with composables
```vue
<template>
  <img v-for="(dog, index) in dogs" :src="dog" :key="index" alt="Dog" />
</template>

<script setup>
  import useDogImages from "../composables/useDogImages";

  const { dogs } = useDogImages();
</script>
```


# Data Provider Component Pattern 
+ The recommendation is to use composables when reusing pure logic, and use components when reusing both logic and visual layout.
```vue
<template>
  <DataProvider v-slot="{ data, loading }">
    <!-- ... -->
  </DataProvider>
</template>

<script setup>
  import DataProvider from "./components/DataProvider.vue";
</script>
```
+ this pattern can be replaced with composables
```vue
<template>
  <div class="joke-section">
    <p v-if="loading">Joke is loading...</p>
    <p v-if="!loading">{{ data.setup }}</p>
    <p v-if="!loading">{{ data.punchline }}</p>
  </div>
</template>

<script setup>
  import { useGetJoke } from "./composables/useGetJoke";

  const { data, loading } = useGetJoke();
</script>
```
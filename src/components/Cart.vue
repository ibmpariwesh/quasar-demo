<template>
  test
  <div class="q-pa-md" style="max-width: 350px">
    <q-list bordered separator v-for="item in items" :key="item">
      <q-item clickable v-ripple>
        <q-item-section>
          <q-item-label>{{ item.name }}</q-item-label>
             <q-item-label>{{ item.price }}</q-item-label>
             </q-item-section
        >
      </q-item>
    </q-list>
  </div>
</template>

<script>
export default {
  name: "CartC",
  data() {
    return {
      items: ["A", "B", "C"],
    };
  },
  mounted() {
    console.log("test");
    const promise = fetch("http://localhost:3000/items");
    promise.then((response) => {
      response.json().then((items) => (this.items = items));
    });
  },
};
</script>

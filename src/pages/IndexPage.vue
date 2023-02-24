<template>
  <q-page class="flex flex-center">
     <Cart></Cart>

  </q-page>
</template>

<script>
import { defineComponent } from 'vue'
import { Cart } from "../components/Cart.vue";
export default defineComponent({
  name: 'IndexPage',
  methods: {
    save:function () {
      console.log('test');
    }
  },
  components:{Cart}
})
</script>

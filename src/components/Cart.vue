<template>
  <div class="q-pa-md" style="max-width: 350px">
    <div class="q-pa-md" style="max-width: 400px">

      <q-form  @reset="onReset" class="q-gutter-md">
        <q-input filled v-model="item.name" label="Your name *" hint="Name and surname" lazy-rules
          :rules="[val => val && val.length > 0 || 'Please type something']" />

        <q-input filled type="number" v-model="item.price" label="Your age *" lazy-rules :rules="[
          val => val !== null && val !== '' || 'Please type your age',
          val => val > 0 && val < 1000000 || 'Please type a real age'
        ]" />

        <q-toggle v-model="accept" label="I accept the license and terms" />

        <div>
          <q-btn label="Submit" type="submit" @click='save' color="primary" />
          <q-btn label="Reset" type="reset" color="primary" flat class="q-ml-sm" />
        </div>
      </q-form>

    </div>

    <q-list bordered separator v-for="item in items" :key="item">
      <q-item>
        <q-item-section>
          <q-item-label>{{ item.name }}</q-item-label>
        </q-item-section>
        <q-item-section>
          <q-item-label>{{ item.price }}</q-item-label>
        </q-item-section>
        <q-item-section>
          <q-btn class="glossy" round color="deep-orange" icon="local_activity" />
        </q-item-section>
      </q-item>
    </q-list>
  </div>
</template>

<script>
export default {
  name: "CartC",
  data() {
    return {
      item:{
        name:'IPhone',
        price:30000
      },
      items: [],
    };
  },
  methods:{
    async save(){
      //ajax
    const response = await fetch("http://localhost:3000/items",{
      method:'post',
      body: JSON.stringify(Object.assign({}, this.item)),
      headers:{
        'content-type':'application/json'
      }
    });
      // this.
      console.log('ajax');
    }
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

<template>
  <main>
    <div class="album py-5 bg-light">
      <div class="container">
        <div class="row row-cols-1 row-cols-sm-2 row-cols-md-3 g-3">
          <div class="col" v-for="(item, idx) in state.items" :key="idx">
            <Card :item="item" />
          </div>
        </div>
      </div>
    </div>
  </main>
</template>

<script>
import Card from "@/components/Card.vue";
import axios from "axios";
import { reactive } from "vue";
export default {
  components: { Card },
  data() {
    return {
      sampleData: "",
    };
  },
  setup() {
    const state = reactive({
      items: [],
    });
    axios.get("/api/items").then(({ data }) => {
      //console.log(res);
      state.items = data;
    });

    return { state };
  },
  created() {},
  mounted() {},
  unmounted() {},
  methods: {},
};
</script>

<style scoped></style>

<template>
  <div class="card shadow-sm">
    <div class="img" :style="{ backgroundImage: `url(${item.imgPath})` }"></div>

    <!-- 프로필사진 -->

    <div class="card-body">
      <p class="card-text">
        {{ item.name }} &nbsp;
        <span class="discount badge bg-danger">{{ item.discountPer }}%</span>
      </p>
      <div class="d-flex justify-content-between align-items-center">
        <div class="btn-group">
          <button class="btn btn-primary">구입하기</button>
        </div>
        <small class="price text-muted">{{ lib.getNumberFormatted(item.price) }}원</small>

        <small class="real text-muted">{{ lib.getNumberFormatted(item.price - (item.price * item.discountPer) / 100) }}원</small>
      </div>
    </div>
  </div>
</template>

<script>
import lib from '@/scripts/lib'
export default {
  name: 'Card',
  props: {
    item: Object
  },
  components: {},
  data() {
    return {
      sampleData: ''
    }
  },
  setup() {
    return { lib }
  },
  created() {},
  mounted() {},
  unmounted() {},
  methods: {}
}
</script>

<style scoped>
.card .img {
  display: inline-block;
  width: 100%;
  height: 250px;
  background-size: cover;
  background-position: center;
}

.card .card-body .price {
  text-decoration: line-through;
}
.card .card-body .real {
  font-weight: bold;
  font-size: 16px;
}
</style>

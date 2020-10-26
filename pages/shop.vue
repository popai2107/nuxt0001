<template>
  <div>
    <h1>Shop</h1>
    <ul>
      <li v-for="(i, index) in 10" :key="index">
        สินค้า {{ i }}
        รูปภาพสินค้า ราคา ส่วนลด
        <nuxt-link :to="{ name: 'product-id', params: { id: i } }"
          >ปุ่มดูรายละเอียด</nuxt-link
        >
        ปุ่มสั่งซื้อ
      </li>
    </ul>
  </div>
</template>

<script>
export default {}
</script>

<style></style>

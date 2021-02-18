<template>
  <div class="container py-5">
    <div>
      <h1>{{ restaurant.name }}</h1>
      <span class="badge badge-secondary mt-1 mb-3">
        {{ restaurant.Category ? restaurant.Category.name : "未分類" }}
      </span>
    </div>

    <hr />

    <ul>
      <li>評論數： {{ restaurant.Comments.length }}</li>
      <li>瀏覽次數： {{ restaurant.viewCounts }}</li>
    </ul>

    <button type="button" class="btn btn-link" @click="$router.back()">
      回上一頁
    </button>
  </div>
</template>

<script>
const dummyData = {
  // 請貼上資料樣本
  restaurant: {
    id: 9,
    name: "Esteban Conn",
    tel: "(925) 432-9834 x4118",
    address: "2245 Jalon Vista",
    opening_hours: "08:00",
    description: "Magnam autem sed id molestiae nihil quia.",
    image:
      "https://loremflickr.com/320/240/restaurant,food/?random=9.434835967288935",
    viewCounts: 60,
    createdAt: "2020-12-15T06:35:43.000Z",
    updatedAt: "2021-02-18T13:58:33.000Z",
    CategoryId: 1,
    Category: null,
    Comments: [],
  },
};

export default {
  name: "RestaurantDashboard",
  data() {
    return {
      restaurant: {},
    };
  },
  created() {
    this.restaurant = { ...dummyData.restaurant };
    console.log(this.restaurant);
    console.log(this.$route.params);
  },
};
</script>
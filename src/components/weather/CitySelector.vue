<template>
  <div>
    <ul class="city-selector">
      <li
        @click="selectCity(city)"
        :class="{ isSelected: city.selected }"
        v-for="city in cities"
        :key="city.code"
      >
        {{ city.label }}
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "CitySelector",
  data() {
    return {
      cities: [
        { code: "seoul", label: "서울", selected: false },
        { code: "porto", label: "포르투", selected: false },
        { code: "hawaii", label: "하와이", selected: false },
        { code: "dubrovnik", label: "두브로브니크", selected: false },
        { code: "lausanne", label: "로잔", selected: false },
        { code: "capri", label: "카프리", selected: false },
        { code: "london", label: "런던", selected: false },
        { code: "bali", label: "발리", selected: false },
      ],
    };
  },
  methods: {
    selectCity(city) {
      city.selected = !city.selected;
      this.$emit("selectCity", city);
    },
  },
};
</script>

<style scoped>
.city-selector {
  display: grid;
  grid-template-columns: repeat(5, 1fr);
}
.city-selector li {
  display: flex;
  justify-content: center;
  align-items: center;
  border: 0.05em solid #efefef;
  padding: 0.3em;
  cursor: pointer;
}
.isSelected {
  background: #fd1d1d;
  color: #fff;
}
</style>

<template>
  <div class="header">
    <h2>Title</h2>
    <div class="dot-menu">
      <button class="dot-menu__button">
        <svg
          height="25"
          width="25"
          viewBox="0 0 24 24"
          xmlns="http://www.w3.org/2000/svg"
        >
          <circle cx="12" cy="12" r="3" />
          <circle cx="12" cy="3" r="3" />
          <circle cx="12" cy="21" r="3" />
        </svg>
      </button>
      <div class="dot-menu__content">
        <ul class="dot-menu__list">
          <li v-for="item in dotMenuItem" :key="item.name" class="dot-menu__item">{{item.name}}</li>
        </ul>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      dotMenuItem: [
        {name: "Rename list"}, 
        {name: "Sort by"}, 
        {name: "Delete list"},  
      ],
    };
  },
};
</script>

<style lang="scss">
.header {
  width: inherit;
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.dot-menu {
  position: relative;
}

.dot-menu__button {
  padding: 0;
  border: 0;
  background: none;
  & > svg {
    fill: green;
  }
}

.dot-menu__content {
  width: 100px;
  height: 100px;
  border-radius: 5px;
  background: yellow;
  position: absolute;
  right: 0;
  top: 0;
}
</style>
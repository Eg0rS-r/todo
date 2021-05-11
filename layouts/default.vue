<template>
  <div class="wrapper">
    <transition name="slide-top">
      <header class="wrapper-header" v-if="isListOpen">
        <button
          class="btn-blank btn-icon"
          @click="isListOpen = false"
        >
          <svg viewBox="0 0 24 24" class="arrow-left btn-svg">
            <path
              d="M13.025 1l-2.847 2.828 6.176 6.176h-16.354v3.992h16.354l-6.176 6.176 2.847 2.828 10.975-11z"
            />
          </svg>
        </button>

        <!-- <h1 class="h1">
          <span v-if="isListOpen">List</span>
          <span v-else>All lists</span>
      </h1> -->

        <button
          @click="isListStarred = !isListStarred"
          class="btn-blank btn-icon btn-star"
          :class="{ 'btn-star--active': isListStarred }"
        >
          <svg viewBox="0 0 24 24" class="btn-svg">
            <path
              d="M12 .288l2.833 8.718h9.167l-7.417 5.389 2.833 8.718-7.416-5.388-7.417 5.388 2.833-8.718-7.416-5.389h9.167z"
            />
          </svg>
        </button>
      </header>
    </transition>

    <Nuxt />
  </div>
</template>

<script>
import Vue from "vue";
Vue.directive("click-outside", {
  bind(el, binding) {
    el.addEventListener("click", (e) => e.stopPropagation());
    document.body.addEventListener("click", binding.value);
  },
  unbind(el, binding) {
    document.body.removeEventListener("click", binding.value);
  },
});

export default {
  data() {
    return {
      isListOpen: true,
      isListStarred: false,
    };
  },
};
</script>

<style lang="scss">
// Default TAG
ul {
  padding: 0;
  margin: 0;
  & > li {
    list-style-type: none;
  }
}

// Default CLASS

.btn-blank {
  background: none;
  border: none;
  padding: 0;
}

.btn-star {
  transition-duration: 0.4s;
  &--active {
    fill: red;
  }
}

.btn-svg {
  max-width: 35px;
  max-height: 35px;
}

.fade-enter-active,
.fade-leave-active,
.fade-left-enter-active,
.fade-left-leave-active {
  transition: all 0.4s;
}

.fade-enter-from,
.fade-leave-to {
  opacity: 0;
}

.slide-top-enter-from,
.slide-top-leave-to {
  transform: translateY(-100%);
}

.dot-vertical {
  transform: rotate(90deg);
}

.arrow-left {
  transform: rotate(180deg);
}

.wrapper-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 8px 16px;
  transition: all 1s;
  & > h1 {
    margin: 0;
  }

  // DEV
  background-color: green;
}

// DEV FOCUS
button:focus {
  background-color: yellow;
}
</style>

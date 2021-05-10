<template>
  <div class="wrapper">
    <header class="wrapper-header">
      <button class="btn-blank btn-icon">
        <svg
          width="50"
          heigth="50"
          viewBox="0 0 512 512"
          class="arrow-left arrow-left--btn"
        >
          <g>
            <g>
              <path
                d="M388.425,241.951L151.609,5.79c-7.759-7.733-20.321-7.72-28.067,0.04c-7.74,7.759-7.72,20.328,0.04,28.067l222.72,222.105
			L123.574,478.106c-7.759,7.74-7.779,20.301-0.04,28.061c3.883,3.89,8.97,5.835,14.057,5.835c5.074,0,10.141-1.932,14.017-5.795
			l236.817-236.155c3.737-3.718,5.834-8.778,5.834-14.05S392.156,245.676,388.425,241.951z"
              />
            </g>
          </g>
        </svg>
      </button>
      <h1 class="h1">Title</h1>

      <DotMenu />
    </header>

    <Nuxt />
  </div>
</template>

<script>

import Vue from 'vue'
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
  
}
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

.dot-vertical {
  transform: rotate(90deg);
}

.arrow-left {
  transform: rotate(180deg);
  &--btn {
    padding: 6px;
  }
}

.wrapper-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 8px;
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

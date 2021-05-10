<template>
  <div class="dot-menu">
    <button class="btn-blank btn-icon btn-dot-menu" @click="DotMenuOpen">
      <svg width="50" heigth="50" viewBox="0 0 512 512" class="dot-vertical">
        <g>
          <path
            d="M256,224c-17.7,0-32,14.3-32,32s14.3,32,32,32c17.7,0,32-14.3,32-32S273.7,224,256,224L256,224z"
          />
          <path
            d="M128.4,224c-17.7,0-32,14.3-32,32s14.3,32,32,32c17.7,0,32-14.3,32-32S146,224,128.4,224L128.4,224z"
          />
          <path
            d="M384,224c-17.7,0-32,14.3-32,32s14.3,32,32,32s32-14.3,32-32S401.7,224,384,224L384,224z"
          />
        </g>
      </svg>
    </button>
    <div v-show="isDotMenuOpen" class="dot-menu__content">
      <ul class="dot-menu__list">
        <li class="dot-menu__item">
          <button class="btn-blank">
            <svg width="24" height="24" viewBox="0 0 24 24">
              <path
                d="M14.078 7.061l2.861 2.862-10.799 10.798-3.584.723.724-3.585 10.798-10.798zm0-2.829l-12.64 12.64-1.438 7.128 7.127-1.438 12.642-12.64-5.691-5.69zm7.105 4.277l2.817-2.82-5.691-5.689-2.816 2.817 5.69 5.692z"
              />
            </svg>
            <span class="dot-menu__title">Edit title</span>
          </button>
        </li>
        <li class="dot-menu__item">
          <button class="btn-blank">
            <svg width="24" height="24" viewBox="0 0 24 24">
              <path
                d="M12 6.76l1.379 4.246h4.465l-3.612 2.625 1.379 4.246-3.611-2.625-3.612 2.625 1.379-4.246-3.612-2.625h4.465l1.38-4.246zm0-6.472l-2.833 8.718h-9.167l7.416 5.389-2.833 8.718 7.417-5.388 7.416 5.388-2.833-8.718 7.417-5.389h-9.167l-2.833-8.718z"
              />
            </svg>
            <span class="dot-menu__title">Starred</span>
          </button>
        </li>
        <li class="dot-menu__item">
          <button class="btn-blank">
            <svg width="24" height="24" viewBox="0 0 24 24">
              <path
                d="M21 6l-3 18h-12l-3-18h2.028l2.666 16h8.611l2.666-16h2.029zm-4.711-4c-.9 0-1.631-1.099-1.631-2h-5.316c0 .901-.73 2-1.631 2h-5.711v2h20v-2h-5.711z"
              />
            </svg>
            <span class="dot-menu__title">Delete</span>
          </button>
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  name: 'testName',
  data() {
    return {
      isDotMenuOpen: false,
    };
  },
  methods: {
    DotMenuOpen() {
      var isDotMenuOpen2 = this.isDotMenuOpen
      this.isDotMenuOpen = true;
      function DotMenuEvent(e) {
        let target = e.target;
        while (target != document.body) {
          if (
            target == document.querySelector(".btn-dot-menu") ||
            target == document.querySelector(".dot-menu__content")
          ) {
            console.log("NOT");
            return;
          }
          target = target.parentNode;
        }
        isDotMenuOpen2 = false;
        console.log("nothing");
        document.body.removeEventListener("click", DotMenuEvent);
      }
      document.body.addEventListener("click", DotMenuEvent);
    },
  },
};
</script>

<style lang="scss">
.dot-menu {
  position: relative;
}
.dot-menu__content {
  position: absolute;
  right: 0;
  top: 0;
  padding: 10px 20px;
  border-radius: 5px;

  // DEV
  background-color: red;
}

.dot-menu__list {
  min-width: max-content;
}

.dot-menu__item {
  margin-bottom: 8px;
  & > button {
    display: flex;
    align-items: center;
    padding: 8px 0px;
    width: 100%;
  }
  &:last-child {
    margin-bottom: 0;
  }
}

.dot-menu__title {
  margin-left: 8px;
}
</style>
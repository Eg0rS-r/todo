<template>
  <div class="main">
    <h2>List of Lists</h2>

    <ul class="list-group" v-if="isListSelect">
      <li
        v-for="list in lists"
        :key="list.title"
        class="list-group-item list-group-item--lists"
      >
        <button class="btn-blank btn-blank--lists" @click="listOpen(list)">
          {{ list.title }}
          <svg
            class="list-group-item-img"
            xmlns="http://www.w3.org/2000/svg"
            viewBox="0 0 512.002 512.002"
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
      </li>
    </ul>

    <ul class="task-list" v-else>
      <li
        v-for="item in outList.tasks"
        :key="item.name"
        class="task-list-item"
        :style="{ order: item.orderId }"
      >
        <button
          class="btn-blank btn-blank--lists"
          :class="[item.check ? 'btn-blank--check' : '']"
          @click="taskCheck(item)"
        >
          {{ item.name }}

          <svg
            height="512pt"
            viewBox="0 0 512 512"
            width="512pt"
            xmlns="http://www.w3.org/2000/svg"
            class="list-group-item-check"
          >
            <path
              v-if="item.check"
              d="
              m 375 200
              c 7 7 7 20 0 28
              l-134 134
              c-7 7-20 7-28 0
              l-63-63
              c-7-7-7-20 0-28 7-7 20-7 28 0
              l 49 49 120-120
              c 7-7 20-7 28 0z
            "
            />

            <path
              d="m512 256
              c0 141.503906-114.515625 256-256 256-141.503906 0-256-114.515625-256-256 0-141.503906 114.515625-256 256-256 141.503906 0 256 114.515625 256 256z
              m-40 0
              c0-119.394531-96.621094-216-216-216-119.394531 0-216 96.621094-216 216 0 119.394531 96.621094 216 216 216 119.394531 0 216-96.621094 216-216z
              m0 0"
            />
          </svg>
        </button>
      </li>
    </ul>

    <button
      type="button"
      class="btn btn--right-bottom btn-primary"
      @click="isListAdd = !isListAdd"
      aria-label="Add list"
    >
      <svg
        height="426.66667pt"
        alt="plus"
        viewBox="0 0 426.66667 426.66667"
        width="426.66667pt"
        xmlns="http://www.w3.org/2000/svg"
      >
        <path
          d="m405.332031 192h-170.664062v-170.667969c0-11.773437-9.558594-21.332031-21.335938-21.332031-11.773437 0-21.332031 9.558594-21.332031 21.332031v170.667969h-170.667969c-11.773437 0-21.332031 9.558594-21.332031 21.332031 0 11.777344 9.558594 21.335938 21.332031 21.335938h170.667969v170.664062c0 11.777344 9.558594 21.335938 21.332031 21.335938 11.777344 0 21.335938-9.558594 21.335938-21.335938v-170.664062h170.664062c11.777344 0 21.335938-9.558594 21.335938-21.335938 0-11.773437-9.558594-21.332031-21.335938-21.332031zm0 0"
        />
      </svg>
    </button>

    <div class="modal" v-if="isListAdd">
      <div class="modal__back" @click="isListAdd = !isListAdd"></div>
      <div class="modal__content">
        <label for="listTitle">Enter list title</label>

        <input
          type="text"
          class="form-control"
          id="listTitle"
          placeholder="New list"
        />
        <div class="modal__button">
          <button type="button" class="btn btn--modal btn-secondary" @click="isListAdd = !isListAdd">Cancel</button>
          <button type="button" class="btn btn-primary" @click="listAdd">Confirm</button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      isListSelect: true,
      isListAdd: false,
      lists: [
        {
          title: "Today",
          listId: 0,
          tasks: [
            {
              name: "1 task Today",
              check: false,
              orderId: 1,
            },
            {
              name: "2 task Today",
              check: false,
              orderId: 2,
            },
            {
              name: "3 task Today",
              check: false,
              orderId: 3,
            },
            {
              name: "4 task Today",
              check: false,
              orderId: 4,
            },
            {
              name: "5 task Today",
              check: false,
              orderId: 5,
            },
          ],
        },
        {
          title: "Study",
          listId: 1,
          tasks: [
            {
              name: "1 task Study",
              check: false,
              orderId: 1,
            },
            {
              name: "2 task Study",
              check: false,
              orderId: 2,
            },
            {
              name: "3 task Study",
              check: false,
              orderId: 3,
            },
            {
              name: "4 task Study",
              check: false,
              orderId: 4,
            },
            {
              name: "5 task Study",
              check: false,
              orderId: 5,
            },
          ],
        },
        {
          title: "Everyday",
          listId: 2,
          tasks: [
            {
              name: "1 task Everyday",
              check: false,
              orderId: 1,
            },
            {
              name: "2 task Everyday",
              check: false,
              orderId: 2,
            },
            {
              name: "3 task Everyday",
              check: false,
              orderId: 3,
            },
            {
              name: "4 task Everyday",
              check: false,
              orderId: 4,
            },
            {
              name: "5 task Everyday",
              check: false,
              orderId: 5,
            },
          ],
        },
        {
          title: "Work",
          listId: 3,
          tasks: [
            {
              name: "1 task Work",
              check: false,
              orderId: 1,
            },
            {
              name: "2 task Work",
              check: false,
              orderId: 2,
            },
            {
              name: "3 task Work",
              check: false,
              orderId: 3,
            },
            {
              name: "4 task Work",
              check: false,
              orderId: 4,
            },
            {
              name: "5 task Work",
              check: false,
              orderId: 5,
            },
          ],
        },
      ],
      outTasks: null,
    };
  },
  methods: {
    saveList() {
      localStorage.setItem("itemList", JSON.stringify(this.itemList));
      console.log("save list");
    },
    getList() {
      this.itemList = JSON.parse(localStorage.getItem("itemList"));
      console.log("get list");
    },
    listAdd() {

      this.isListAdd = !this.isListAdd
      console.log("add");
    },
    listOpen(list) {
      this.outList = list;
      this.isListSelect = false;
    },
    taskCheck(task) {
      task.check = !task.check;
      task.orderId = this.outList.tasks.length + 1;
    },
  },
  computed: {},
};
</script>

<style lang="scss">
.list-group-item {
  &--lists {
    padding: 0;
  }
  &:hover {
    background-color: #fbfbfb;
  }
  &:hover .list-group-item-img {
    margin-right: 5px;
  }
}

.list-group-item-img {
  width: 22px;
  height: 22px;
  transition-duration: 0.3s;
}

.btn-blank--lists {
  width: 100%;
  display: flex;
  justify-content: space-between;
  padding: 0.75rem 1.25rem;
  // DEV
  &:focus {
    background-color: yellow;
  }
}

.alert-light--task {
  width: 100%;
  text-align: left;
}

.list-group-item-check {
  width: 23px;
  height: 23px;
  margin: 1px;
  border-radius: 50%;
  fill: #646464;
}
</style>
<template>
  <div class="row">
    <div class="col-2">
      <button class="btn btn-secondary button" @click="sort">
        To original order
      </button>
    </div>

    <div class="col-6">
      <h3>Transition</h3>
      <draggable
        class="list-group"
        item-key="order"
        tag="transition-group"
        :component-data="{ tag: 'ul', name: 'flip-list', type: 'transition' }"
        v-model="list"
        v-bind="dragOptions"
        @start="isDragging = true"
        @end="isDragging = false"
      >
        <template #item="{ element }">
          <li class="list-group-item">
            <header>
              {{ element.name }}
            </header>
            <article>
              {{ element.order }} |
              <span :class="element.status == 'open' ? 'open' : 'close'">{{ element.status }}</span>
            </article>
          </li>
        </template>
      </draggable>
    </div>
  </div>
</template>

<script>
import draggable from 'vuedraggable';
import Projects from '../services/Projects.vue';

export default {
  name: 'Projects_Twitch',
  display: 'Transition',
  order: 6,
  components: {
    draggable,
  },
  async setup() {
    const project = await Projects.get();
    return {
      list: project.map((data, index) => ({
        id: data.id, name: data.name, status: data.status, order: index + 1,
      })),
      order: project.length,
    };
  },
  methods: {
    sort() {
      this.list = this.list.sort((a, b) => a.order - b.order);
    },
  },
  computed: {
    dragOptions() {
      return {
        animation: 200,
        group: 'description',
        disabled: false,
        ghostClass: 'ghost',
      };
    },
  },
};
</script>

<style>
.button {
  margin-top: 35px;
}
.flip-list-move {
  transition: transform 0.5s;
}
.no-move {
  transition: transform 0s;
}
.ghost {
  opacity: 0.5;
  background: #c8ebfb;
}
.close{
  color: red;
}
.open{
  color: green;
}
ul{
  display: grid;
  place-items: center;
  margin: 0 ;
  padding: 0;
}
.list-group {
  min-height: 20px;
}
.list-group-item {
  margin-bottom: 10px;
  padding: 20px;
  width: 30%;
  border: 1px solid black;
  list-style: none;
  cursor: move;
}
.list-group-item i {
  cursor: pointer;
}
</style>

<template>
  <section>
    <h2 class="title">Filters</h2>
    <b-collapse v-for="(type, index) of filterTypes" :key="index" :open="true">
      <h4 slot="trigger" slot-scope="props">
        {{ type.name }} <a>{{ props.open ? '-' : '+' }}</a>
      </h4>
      <ul>
        <li v-for="filter of type.filters" :key="filter.id">
          <b-checkbox
            :native-value="filter.id"
            :value="currentFilters"
            @input="$emit('change', $event)"
          >
            {{ filter.name }}
          </b-checkbox>
        </li>
      </ul>
    </b-collapse>
  </section>
</template>

<script>
export default {
  props: {
    filterTypes: {type: Array, default: () => []},
    currentFilters: {type: Array, default: () => []},
  },
  model: {
    prop: 'currentFilters',
    event: 'change',
  },
}
</script>

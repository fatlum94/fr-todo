<template>
    <v-text-field
        placeholder="Search"
        :class="{'closed': searchClosed && !$store.state.search}"
        @focus="searchClosed = false"
        @blur="searchClosed = true"
        @input="$store.commit('setSearch', $event)"
        :value="$store.state.search"
        filled
        dense
        clearable
        prepend-inner-icon="mdi-magnify"
        class="mt-1 expanding-search"
    ></v-text-field>
</template>

<script>
export default {
    data(){
        return {
            searchClosed: true
        }
    }
}
</script>

<style lang="sass">
    .expanding-search
     transition: max-width 0.3s
     .v-input__slot
      cursor: pointer !important
      &:before, &:after
        border-color: transparent !important
     &.closed
        max-width: 45px
        .v-input__slot
         background: transparent !important

</style>
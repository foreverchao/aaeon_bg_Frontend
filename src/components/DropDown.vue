<template>
    <div class="text-center">
    <v-menu offset-y>
      <template v-slot:activator="{ on, attrs }">
        <v-btn
          color="primary"
          dark
          v-bind="attrs"
          v-on="on">
            <slot></slot>
        </v-btn>
      </template>

      <v-list>
        <v-list-item
          v-for="(item, index) in items"
          :key="index"
        >
          <v-list-item-title>{{ item.title }}</v-list-item-title>
        </v-list-item>
      </v-list>
    </v-menu>
  </div>
</template>
  
<script>
  export default {
    name: 'DropDown',
    data: () => ({
      items: [
        { title: '繁體中文' },
        { title: 'English' },
      ],
    }),
  }
</script>
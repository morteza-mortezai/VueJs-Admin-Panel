<template>
  <v-card class="px-5 pt-3 pb-1"  flat outlined>
    <v-list-item>
        <v-icon size="50" color="red">mdi-{{cardData.icon}}</v-icon>
      <v-list-item-content class="text-right">
        <v-list-item-title>{{cardData.title}}</v-list-item-title>
        <v-list-item-subtitle>{{cardData.subtitle}}</v-list-item-subtitle>
      </v-list-item-content>
    </v-list-item>
    <v-divider class="mt-2 mb-0" />
    <v-list-item>
      <v-list-item-avatar>
        <v-icon>
          mdi-{{cardData.secondIcon}}
        </v-icon>
      </v-list-item-avatar>
      <v-list-item-title>
       {{cardData.detail}}
      </v-list-item-title>
    </v-list-item>
  </v-card>
</template>
<script>
export default {
  name: "ccard",
  props:['cardData']
};
</script>

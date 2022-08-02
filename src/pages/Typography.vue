<template>
  <q-page class="flex column q-pa-md">
    <!-- <h1>Typography</h1> -->
    <span class="text-h1">Headline 1</span>
    <span class="text-h2">Headline 2</span>
    <span class="text-h3">Headline 3</span>
    <span class="text-h4">Headline 4</span>
    <span class="text-h5">Headline 5</span>
    <span class="text-h6">Headline 6</span>
    <q-separator></q-separator>
    <span class="text-subtitle1">Subtitle 1</span>
    <span class="text-subtitle2">Subtitle 2</span>
    <q-separator />
    <p class="text-body1">
      Lorem ipsum dolor sit amet consectetur adipisicing elit. Animi eius velit
      adipisci reiciendis aliquid voluptatem consequuntur distinctio consectetur
      obcaecati ex! Sed sapiente, dolorem accusantium est excepturi fugit
      placeat explicabo earum!
    </p>
    <p class="text-body2 text-right">
      Lorem ipsum dolor sit amet consectetur adipisicing elit. Animi eius velit
      adipisci reiciendis aliquid voluptatem consequuntur distinctio consectetur
      obcaecati ex! Sed sapiente, dolorem accusantium est excepturi fugit
      placeat explicabo earum!
    </p>

    <q-btn
      @click="toggleSideMenu"
      color="primary"
      :label="sideMenuOpen ? 'Cerrar menu lateral' : 'Abrir menú lateral'"
      class="q-mt-md"
    >
    </q-btn>
  </q-page>
</template>

<script>
import { defineComponent } from "vue";
import useUI from "../composable/useUI.js";

export default defineComponent({
  name: "Typography",
  setup() {
    const { sideMenuOpen, toggleSideMenu } = useUI();

    return {
      toggleSideMenu,
      sideMenuOpen,
    };
  },
});
</script>

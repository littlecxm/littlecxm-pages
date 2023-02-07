<template>
  <div>
    <Header />
    <NBackTop :listen-to="target" :visibility-height="10" />
    <NLayout
      :style="{
        maxWidth: '100%',
        margin: 'auto auto',
        paddingTop: 'var(--header-height)',
      }"
    >
      <NLayout
        ref="layoutInstRef"
        :content-style="{
          minHeight: 'calc(90vh - var(--header-height))',
        }"
      >
        <router-view />
      </NLayout>
    </NLayout>
    <Footer />
  </div>
</template>

<script setup lang="ts">
import { ref } from "vue";
import { NLayout, NBackTop } from "naive-ui";
import Header from "./header.vue";
import Footer from "./footer.vue";

const layoutInstRef = ref<HTMLElement | undefined>(undefined);
const target = () => layoutInstRef.value;
</script>

<style scoped>
a::before {
  content: "";
  position: absolute;
  left: 0;
  right: 0;
  top: 0;
  bottom: 0;
}
</style>

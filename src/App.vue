<template>
  <div id="app">
    <FishingModal
      title="Удочка (1 уровень)"
      title-color="#02CE0A"
      description="Снасть в виде гибкого хлыста, изготовляемого ранее из дерева (сейчас и из других материалов)"
      :image="require('@/assets/fishing-modal/img/fishing-rods/2.png')"
      :price="90000"
      :weight="1.5"
    />
    <FishingModal
        title="Удочка (2 уровень)"
        title-color="#0A9CFB"
        description="Снасть в виде гибкого хлыста, изготовляемого ранее из дерева (сейчас и из других материалов)"
        :image="require('@/assets/fishing-modal/img/fishing-rods/1.png')"
        :price="90000"
        :weight="1.5"
    />
  </div>
</template>

<script>
import FishingModal from "@/components/fishing-modal/FishingModal";

export default {
  name: 'App',
  components: {
    FishingModal,
  }
}
</script>

<style lang="scss">
@import "./assets/fishing-modal/fonts/roboto/stylesheet.css";

#app {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: .25vw;

  width: 100%;
  height: 100vh;
}

* {
  margin: 0;
  padding: 0;

  font-family: 'Roboto';
}
</style>

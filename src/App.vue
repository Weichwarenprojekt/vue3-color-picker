<template>
    <div class="app">
        <ColorPicker></ColorPicker>
    </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import ColorPicker from "@/color-picker/ColorPicker.vue";

export default defineComponent({
    name: "App",
    components: {
        ColorPicker,
    },
});
</script>

<style lang="less">
@import "styles/global";

.app {
    padding: 16px;
}
</style>

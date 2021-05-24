<template>
    <div class="color-picker">
        <!-- The select mode tabs -->
        <div class="color-picker-tabs">
            <div
                v-for="mode in selectModes"
                @click="selectMode = mode"
                :class="['color-picker-tab', { 'color-picker-tab-active': selectMode === mode }]"
            >
                {{ mode }}
            </div>
        </div>
        <!-- The input mode tabs -->
        <div class="color-picker-tabs">
            <div
                v-for="mode in inputModes"
                @click="inputMode = mode"
                :class="['color-picker-tab', { 'color-picker-tab-active': inputMode === mode }]"
            >
                {{ mode }}
            </div>
        </div>
    </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import { SelectModes } from "@/color-picker/models/SelectModes";
import { InputModes } from "@/color-picker/models/InputModes";

export default defineComponent({
    name: "ColorPicker",
    data() {
        return {
            // Forward the select modes so that they are accessible within the template
            selectModes: SelectModes,
            // Forward the input modes so that they are accessible within the template
            inputModes: InputModes,
            // The active select mode
            selectMode: SelectModes.NORMAL as string,
            // The active input mode
            inputMode: InputModes.RGB as string,
        };
    },
});
</script>

<style lang="less">
@import "~@/styles/vars";

.color-picker {
    border-radius: @border-radius;
    box-shadow: 0 3px 10px 0 grey;
    width: 200px;
    height: 200px;
    padding: 8px;
}

.color-picker-tabs {
    background: @grey;
    display: flex;
    border-radius: @border-radius;
    padding: 2px;
    margin-bottom: 8px;
}

.color-picker-tab {
    cursor: pointer;
    flex: 1 1 auto;
    padding: 2px;
    font-size: 8px;
    text-align: center;
    background: transparent;
    border-radius: @border-radius;
}

.color-picker-tab-active {
    background: white;
}
</style>

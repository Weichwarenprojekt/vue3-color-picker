<template>
    <div class="color-picker">
        <!-- The select mode tabs -->
        <div class="color-picker-tabs" v-if="showSelects">
            <div
                v-for="mode in selectModes"
                @click="selectMode = mode"
                :class="['color-picker-tab', { 'color-picker-tab-active': selectMode === mode }]"
            >
                {{ mode }}
            </div>
        </div>

        <!-- The selects -->
        <div ref="selectCanvas" class="color-picker-select" v-if="showSelects">
            <div class="color-picker-select-area"></div>
        </div>

        <!-- The input mode tabs -->
        <div class="color-picker-tabs" v-if="showInputs">
            <div
                v-for="mode in inputModes"
                @click="inputMode = mode"
                :class="['color-picker-tab', { 'color-picker-tab-active': inputMode === mode }]"
            >
                {{ mode }}
            </div>
        </div>
        <!-- The inputs -->
        <div class="color-picker-input" v-if="showInputs">Input</div>

        <!-- The hex value -->
        <div class="color-picker-tabs" v-if="showHEX">
            <div class="color-picker-tab">HEX</div>
        </div>

        <!-- The hex value -->
        <div class="color-picker-tabs" v-if="showOpacity">
            <div class="color-picker-tab">Opacity</div>
        </div>
    </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import { SelectModes } from "@/color-picker/models/SelectModes";
import { InputModes } from "@/color-picker/models/InputModes";

export default defineComponent({
    name: "ColorPicker",
    props: {
        // True if the selects shall be shown
        showSelects: {
            type: Boolean,
            default: true,
        },
        // True if the inputs shall be shown
        showInputs: {
            type: Boolean,
            default: true,
        },
        // True if the hex value tab shall be shown
        showHEX: {
            type: Boolean,
            default: true,
        },
        // True if the opacity value tab shall be shown
        showOpacity: {
            type: Boolean,
            default: true,
        },
    },
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

<style lang="less" scoped>
@import "~@/styles/vars";

.color-picker {
    border-radius: @border-radius;
    box-shadow: 0 3px 10px 0 grey;
    width: 300px;
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
    font-size: 9px;
    text-align: center;
    background: transparent;
    border-radius: @border-radius;
    user-select: none;
}

.color-picker-tab-active {
    background: white;
}

.color-picker-select {
    border-radius: @border-radius;
    background: red;
    height: 150px;
    margin-bottom: 16px;
}

.color-picker-input {
    height: 100px;
    margin-bottom: 16px;
    font-size: 12px;
}
</style>

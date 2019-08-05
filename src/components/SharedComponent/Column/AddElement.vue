<template>
    <div class="custom-add-element"
    @dragover.prevent @drop="handleDrop">
        <div class="custom-add-element-item" @click.stop="$emit('handleAddElement')">
            add element
        </div>
    </div>
</template>
<script>
export default {
    data() {
        return {
            mouseOnElement: false
        }
    },
    methods: {
        handleDrop() {
            this.$emit("handleElementDrop")
        },
    },
}
</script>

<style>
.custom-add-element {
    border-radius: 4px;
    background: rgba(255,116,2,0.1);
    border: 1px solid rgba(255,116,2,0.2);
    border-radius: 5px;
    text-align: center;
    padding: 7px;
    transition: all 0.2s ease-in-out 0s;
    display: flex;
    justify-content: center;
}
.custom-add-element-item{
    background: #fff;
    color: #ff7402;
    font-weight: bold;
    padding: 6px; 
    width: 150px;
    border-radius: 5px;
    cursor: pointer;
}
</style>


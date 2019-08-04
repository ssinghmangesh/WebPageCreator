<template>
    <div>
        {{ data || 'Click here to edit the text'}}
    </div>
</template>
<script>
export default {
    props: {
        elementData: {
            type: Object,
            required: true
        },
    },
    computed: {
        style() {
            return {
                color: "#2a3135",
                fontWeight: "normal",
                fontSize:'16px'
            }
        },
        data() {
            return this.elementData.data
        }
    }
}
</script>
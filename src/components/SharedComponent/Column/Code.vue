<template>
    <div>
        <pre :style="style">
<label>Code</label>
<code>{{ data || 'Click here to edit the text'  }}</code></pre>
    </div>
</template>
<script>
export default {
    props: {
        elementData: {
            type: Object,
            required: true
        }
    },
    computed: {
        style() {
            return {
                color: "#ffa726",
                background: "#333",
                fontSize:'26px',
                padding:"20px",
                borderRadius:"5px"
            }
        },
        data() {
            return this.elementData.data
        }
    }
}
</script>


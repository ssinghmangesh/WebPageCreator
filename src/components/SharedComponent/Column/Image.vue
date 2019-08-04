<template>
    <div :style="style">
        <img :src="data" :style="imageStyle" alt="add image">
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
        imageStyle() {
            if(this.elementData.style){
                const { width, height }= this.elementData.style
                return {
                    width: (width  || '100')+ 'px',
                    height: (height || '100')+ 'px'
                }
            } else {
                return {
                    width: '100px',
                    height: '100px'
                }
            }
        },
        style() {
            return {
                color: "#2a3135",
                fontWeight: "normal",
                fontSize:'26px',
            }
        },
        data() {
            return this.elementData.data
        }
    }
}
</script>


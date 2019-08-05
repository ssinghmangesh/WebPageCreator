<template>
    <div>
        <HeadingHandle 
            v-if="elementType === 'heading'"
            :elementData="elementData"
            @submited="submited"
        />
        <DisplayImageHandle 
            v-else-if="elementType === 'image'"
            :elementData="elementData"
            @submited="submited"
        />
        <CodeHandle
            v-else-if="elementType === 'code'"
            :elementData="elementData"
            @submited="submited"
        />
        <ParagraphHandle 
            v-else-if="elementType === 'paragraph'"
            :elementData="elementData"
            @submited="submited"
        />
    </div>
</template>
<script>

import HeadingHandle from './HeadingHandle'
import DisplayImageHandle from './ImageHandle'
import CodeHandle from './CodeHandle'
import ParagraphHandle from './ParagraphHandle'
export default {
    components: {
        HeadingHandle,
        DisplayImageHandle,
        CodeHandle,
        ParagraphHandle
    },
    props: {
        elementData: {
            type: Object,
            required: true
        }
    },
    computed: {
        elementType() {
            return this.elementData.type
        }
    },
    methods: {
        submited(data) {
            this.$emit("submited", data)
        }
    }

    
}
</script>
<style>
.custom-handle-handle-item{
    margin-bottom: 20px;
}
.custom-handle-handle-item-title {
    margin-bottom: 10px;

}
</style>



<template>
    <div>
        <Heading 
            v-if="elementType === 'heading'"
            :elementData="elementData"
        />
        <DisplayImage 
            v-else-if="elementType === 'image'"
            :elementData="elementData"
        />
        <Code 
            v-else-if="elementType === 'code'"
            :elementData="elementData"
        />
        <Paragraph 
            v-else-if="elementType === 'paragraph'"
            :elementData="elementData"
        />
        <AddElement 
            v-else 
            @handleAddElement="handleAddElement"
            @handleElementDrop="handleElementDrop"
        />
    </div>
</template>
<script>
import Heading from './Heading'
import AddElement from './AddElement'
import DisplayImage from './Image'
import Code from './Code'
import Paragraph from './Paragraph'
export default {
    components: {
        Heading,
        AddElement,
        DisplayImage,
        Code,
        Paragraph
    },
    props: {
        elementDetails: {
            type: Object,
            required: true
        },
        columnIndex: {
            type: Number,
            required: true
        }
    },
    computed: {
        elementType() {
            return this.elementDetails.type
        },
        elementData() {
            return this.elementDetails
        }
    }, 
    methods: {
        handleElementDrop() {
            this.$emit("handleElementDrop", this.columnIndex)
        },
        handleAddElement() {
            const { columnIndex } = this
            let elementPosition = { columnIndex }
            this.$emit("handleAddElement", elementPosition)
        }
    }
}
</script>


<script setup>
    const props = defineProps({
        tabid: {
            type:Number,
            default : 1
        }
    })
    // const tabnum=ref(props.tabid)

    const indicatorPosition = computed(() =>{
        if(props.tabid==1) return  "20px"
        else if(props.tabid==2) return "100px"
        else return "168px"
    })
 //   const indicatorPosition = ref("20px")
    const emit = defineEmits(['click-tab'])
    function clickTab(id){
        // tabnum.value=id
        // if(id==1) indicatorPosition.value = "20px"
        // else if(id==2) indicatorPosition.value = "100px"
        // else indicatorPosition.value = "168px"
        emit('click-tab', id)
    }
    // const tabid = ref(0)
  
    // export default {
    //     data(){
    //         return {
    //             tabid: 0, 
    //         }
    //     },
    //     methods: {
    //         clickTab(id){
    //             this.$emit('click-tab', id)
    //         }
    //     },
    // }
</script>

<template>
    <div>
        <header>
            <div id="webtester-logo"></div>
        </header>
        <nav>
            <ul id='tabs'>
                <li><a  @click="clickTab(1)" style="cursor: pointer;">Prepare</a></li>
                <li><a  @click="clickTab(2)" style="cursor: pointer;">Flight</a></li>
                <li><a  @click="clickTab(3)" style="cursor: pointer;">Test</a></li>
            </ul>
            <span id='indicator' :style="{left:indicatorPosition}"></span>
        </nav>
    </div>
</template>

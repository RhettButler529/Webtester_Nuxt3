<script setup>


    const adtag = ref(null)
    const tabnum = ref(1)

    const istab1 = computed(() => {
        if(tabnum.value==1)return "block"
        else return "none"
    })

    const istab2 = computed(() => {
        if(tabnum.value==2)return "block"
        else return "none"
    })
    const istab3 = computed(() => {
        if(tabnum.value==3)return "block"
        else return "none"
    })

    const title = ref('MRAID Test Page')
    const description = ref('My amazing Nuxt app')

    useHead({
        title,
        meta: [
            {
                name: 'description',
                content: description
            }
        ],
        // link: [
        //     { 
        //         rel: 'stylesheet', 
        //         href: '/css/reset.css',
        //     },
        //     { 
        //         rel: 'stylesheet', 
        //         href: '/css/main.css',
        //     },
        //     { 
        //         rel: 'stylesheet', 
        //         href: '/css/devicesize-widget.css',
        //         type: "text/css"
        //     },
        //     { 
        //         rel: 'stylesheet', 
        //         href: '/css/orientation-widget.css',
        //         type: "text/css"
        //     }
        // ],
        script: [
            {
                src: '/public/safari/test',
                body: true
            },
            {
                src: '/public/safari/main',
                body: true
            },
            {
                src: '/public/safari/mraidview',
                body: true
            }
            // ,
            // {
            //     src: '/public/jquery/jquery.min.1.7.2',
            //     body: true
            // },
            // {
            //     src: '/public/jquery/jquery.tools.min',
            //     body: true
            // },
            // {
            //     src: '/public/jquery/jquery.easing.1.3',
            //     body: true
            // },
            // {
            //     src: '/public/jquery/jquery.indicated-tabs',
            //     body: true
            // },
            // {
            //     src: '/public/jquery/jquery.event.drag-2.2',
            //     body: true
            // }
        ]
    })

    
    function switchTab(id){
        tabnum.value = id
    }
    onMounted(() => {
        
     //   testView()
        load()
    })
    // export default {
    //     data() {
    //         return {
    //             adtag: null,
    //             fragmentArea : null, 
    //             tabnum: 1
    //         }
    //     },
    //     methods: {  
    //         switchTab(id) {
    //             this.tabnum = id
    //         }
    //     },
    //     mounted: function (){
    //         this.$nextTick(function(){
    //             load()
    //             adtag = getQueryStringValue('adtag')
    //             if (adtag  && adtag !== '') {
    //                 setTimeout(function () {
    //                     fragmentArea = document.getElementById('adFragment');
    //                     if (fragmentArea) {
    //                         fragmentArea.value =  decodeURIComponent(adtag);
    //                     }
    //                 }, 1000);
    //             }
    //         })
    //     }
    // }
</script>

<template>
    
    <div>
        <link rel="stylesheet" href="/css/reset.css" />
        <link rel="stylesheet" href="/css/main.css">
        <link rel="stylesheet" href="/css/devicesize-widget.css" type="text/css" />
        <link rel="stylesheet" href="/css/orientation-widget.css" type="text/css" />
        <!-- <link rel="stylesheet" href="/jquery/ui-lightness-jquery-ui.css" type="text/css" /> -->
        <div class = "the-header">
            <TheHeader :tabid="tabnum" @click-tab="switchTab"/>
        </div>
        <form id="setup" name="setup" onsubmit="renderAd(); return false">
            <div id="content">
                <!-- <div v-if="tabnum == 1" class = "form-prepare"> -->
                <section :style="{display:istab1}">
                    <FormPrepare @next-tab="switchTab" />
                </section>    
                <!-- </div> -->
                <!-- <div v-show="tabnum == 2" class = "form-flight"> -->
                <section :style="{display:istab2}">    
                    <FormFlight @next-tab="switchTab" />
                </section>    
                <!-- </div> -->
                <!-- <div v-if="tabnum == 3" class = "form-test"> -->
                <section :style="{display:istab3}">    
                    <FormTest/>
                </section>    
                <!-- </div> -->
            </div>
        </form>

        <div class = "the-footer">
            <TheFooter/>
        </div>
    </div>
</template>

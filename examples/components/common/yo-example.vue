
<template>
    <div class="yo-example-com" :class="yoClasses">
        <div ref="yo_example" class="yo-example" v-if="demo||iframe">
            <iframe class="yo-example-browser" v-if="iframe" :src="iframe" width="100%" frameborder="0" height="400"></iframe>
            <template v-if="demo">
                <keep-alive>
                    <component @loaded="loaded" :is="com" :key="com"></component>
                </keep-alive>
            </template>
        </div>
        <div ref="yo_example_code" class="yo-example-code" :class="expand?'expand':''" :style="!expand?(codeHeight?('height:'+codeHeight+'px'):''):''">
            <ul class="nav" v-if="codeHeight!=44">
                <li class="yo-icon-code">
                </li>
                <li class="yo-icon-full">
                </li>
                <li class="yo-icon-copy">
                </li>
            </ul>
            <yo-code :src="root+demo+ext"></yo-code>
            <footer class="footer">
                <yo-button type="text" @click="expand=!expand" :right-icon="expand?'up':'down'">
                    {{expand?langKey('隐藏代码'):langKey('展开代码')}}
                </yo-button>
            </footer>
        </div>
    </div>
</template>
<script>
import components from '../demos'
export default {
    name:'yo-example-com',
    props:{
        iframe:String,
        demo:String,
        root:{
            type:String,
            default:''
        },
        //是否竖直排列   默认水平排列
        vertical:{
            type:Boolean,
            default:false,
        },
        //代码是否展开  默认为demo的实际宽度
        fold:{
            type:Boolean,
            default:false,
        },
        ext:{
            type:String,
            default:'.vue'
        },
    },
    components,
    data(){
        let com=this.demo
        let coms=com.split('/')
        let names=[]
        coms.forEach((item,index)=>{
            let items=item.split('-')
            let _items=[]
            if(index>0){
                items.forEach((_item,index)=>{
                    _item=_item.slice(0,1).toUpperCase()+_item.slice(1)
                    _items.push(_item)
                })
            }else{
                items.forEach((_item,index)=>{
                    if(index>0){
                        _item=_item.slice(0,1).toUpperCase()+_item.slice(1)
                    }
                    _items.push(_item)
                })
            }
            names.push(_items.join(''))
        })
        com=names.join('')
        let codeHeight=44
        if(!this.fold){
            codeHeight=''
        }
        return {
            com,//动态展示的组件
            //是否展开
            expand:false,
            codeHeight,
        }
    },
    computed: {
        yoClasses(){
            return [
                {'yo-example-com-v':this.vertical}
            ]
        }
    },
    mounted(){
        let that=this
        
        // that.$refs.yo_example_code.style.height=that.$refs.yo_example.offsetHeight
    },
    methods: {
        loaded(){
            let that=this
            if(!that.fold){
                that.$nextTick(()=>{
                    let codeHeight=(that.$refs.yo_example.offsetHeight)+30
                    // let realHeight=that.$refs.yo_example_code.offsetHeight
                    if(codeHeight<200){
                        codeHeight=200
                    }
                    // if(codeHeight>realHeight){
                    //     codeHeight=realHeight
                    // }
                    that.codeHeight=codeHeight
                })
            }
        }
    },
}
</script>
<style lang="less">
    @import "../../src/assets/less/components/common/yo-example.less";
</style>
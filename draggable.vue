<template>
    <div>
        <div class="content">
            <draggable v-model="list" animation="500" ghost-class="border_dashed"  :move="getdata" @update="datadragEnd" @start="start" @end="end">
                <transition-group tag="div">
                    <div class="content_item " v-for="(item,index) in list" :key="index">
                        {{item.id}}
                    </div>
                </transition-group>
            </draggable>
        </div>
    </div>
</template>

<script>
    import draggable from 'vuedraggable'
    export default {
        components: {
            draggable
        },
        data() {
            return {
                list: [],
            }
        },
        watch: {},
        computed: {},
        methods: {
            getListArr() {
                // $.ajax({
                //     url: 'http://localhost:9797/addstudent',
                //     type: 'post',
                //     success: result => {
                //         if (result.success) {
                //             this.list = result.data
                //         }
                //     }
                // })
                this.list =  [
                    {id:1,name:'张小1'},
                    {id:2,name:'张小2'},
                    {id:3,name:'张小3'},
                    {id:4,name:'张小4'},
                    {id:5,name:'张小5'},
                    {id:6,name:'张小6'},
                ]
            },
            start(e){
                console.log(e);
                // e.item.setAttribute("class", e.item.getAttribute('class')+' border_dashed');
                // this.element = e.item
            },
            getdata(e) {
                console.log('move', e.dragged);

                // if (this.element) {
                //     let classVal = this.element.getAttribute("class")
                //     console.log(classVal);
                //     classVal.replace('border_dashed',"")
                //     this.element.setAttribute("class", classVal);
                // }
                // let newVal = e.dragged.getAttribute('class')
                // e.dragged.setAttribute("class", newVal+' border_dashed');
                // this.element = e.dragged
            },
            end(e){
                console.log('endture',e);
                //清楚边框样式
                // let newVal = this.element.getAttribute('class').replace('border_dashed','')
                // this.element.setAttribute('class',newVal)
            },
            datadragEnd(e) {
                console.log('end', e);
                //设备放置
            }
        },
        mounted() {
            this.getListArr()
        },
        created() {},
    }
</script>
<style lang="less" scoped>
    .content_item {
        background-color: lightsalmon;
        padding: 2rem;
        display: inline-block;
        border-radius: 10%;
        margin: 10px;
        cursor: pointer;
        box-sizing: border-box;
    }

    .border_dashed {
        border: 2px dashed gray;
        box-sizing: border-box;
    }
</style>
<template>
    <div>
        <Add_head v-if="info!=''" :info="info"></Add_head>
        <div style="height: 20px"></div>
        <div class="context">
            <div>
                <input class="input_title" type="text" placeholder="请输入您的标题" v-model="info.title">
                <div style="width:850px;height:1px;background-color:#dde4eb;margin-top:10px"></div>
                <div style="height: 10px"></div>
                <el-input
                        class="input_context"
                        type="textarea"
                        :rows="35"
                        placeholder="请输入你的内容"
                        v-model="info.content">
                </el-input>
            </div>

        </div>
    </div>
</template>

<script>
    import Add_head from "@/components/Add_head";
    export default {
        name: "Add",
        components: {Add_head},
        data(){
            return{
                info:{
                    title:'',
                    content:'',
                    time:'',
                    accountid:localStorage.getItem('userid'),

                }
            }
        },
        created(){
            this.getData()
            this.getTime()
        },
        methods:{
            getData(){
            },
            getTime(){
                var _this = this;
                let yy = new Date().getFullYear();
                let mm = new Date().getMonth()+1;
                let dd = new Date().getDate();
                let hh = new Date().getHours();
                let mf = new Date().getMinutes()<10 ? '0'+new Date().getMinutes() : new Date().getMinutes();
                let ss = new Date().getSeconds()<10 ? '0'+new Date().getSeconds() : new Date().getSeconds();
                _this.info.time = yy+'-'+mm+'-'+dd+' '+hh+':'+mf+':'+ss;
                console.log(this.info.time)
            }
        }
    }
</script>

<style scoped>
    .context{
        display: flex;
        width: 930px;
        height:800px;
        margin-left: auto;
        margin-right: auto;
        background-color: #FFFFFF;
        box-shadow: 0px 0px 6px 0px rgba(0,0,0,0.16);
        border-radius: 4px;
        padding-left: 60px;
        padding-top: 40px;
    }
    .input_title{
        height: 25px;
        width: 100%;
        font-family: Microsoft YaHei UI;
        font-size: 20px;
        font-weight: normal;
        font-stretch: normal;
        line-height: 22px;
        letter-spacing: 2px;
        color: #333333;
        border: 0;
    }
    .input_context{
        font-family: Microsoft YaHei UI;
        font-size: 14px;
        font-weight: normal;
        font-stretch: normal;
        line-height: 28px;
        letter-spacing: 1px;
        color: #666666;
        border: 0;
    }

</style>
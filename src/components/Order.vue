<template>
    <div class="Order">
        <div class="Order-header">订单管理</div>
        <div class="Order-title">
            <router-link to="/admin/order/unfinished" class="Order-title-item">未完成订单</router-link>
            <router-link v-if="userLevel !== '售票员'" to="/admin/order/finished" class="Order-title-item">订单分析</router-link>
        </div>
        <router-view></router-view>
    </div>
</template>

<script>
export default {
    name: 'cinema',
    data(){
        return{

        }
    },
    computed: {
        userLevel(){
            return this.$store.state.auth.userInfo.userLevel;
        }
    }
}
</script>

<style lang="less" scoped>
    .Order{
        height: calc(~'100% - 90px');
        &-header{
            height: 75px;
            line-height: 75px;
            font-size: 20px;
            margin-left: 20px;
        }
        &-title{
            position: relative;
            height: calc(2*10px + 21px + 2px - 1px);
            border-bottom: 1px solid #BFBFC1;
            &-item{
                display: inline-block;
                padding: 10px 15px;
                margin-left: 10px;
                text-decoration: none;
                color: #000;
                font-size: 16px;
                &:hover{
                    .router-link-active;
                }
            }
            .router-link-active{
                border-top: 2px solid #00843e;
                border-left: 1px solid #BFBFC1;
                border-right: 1px solid #BFBFC1;
                background: #f6f5fa;
                color: #FF6000;
            }
        }
    }
</style>
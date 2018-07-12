<template>
    <div class="side-bar">
        <ul>
            <li>
                <i class="iconfont">&#xe601;</i>
                <div>收银</div>
            </li>
            <li>
                <i class="iconfont">&#xe602;</i>
                <div>店铺</div>
            </li>
            <li>
                <i class="iconfont">&#xe601;</i>
                <div>商品</div>
            </li>
            <li>
                <i class="iconfont">&#xe603;</i>
                <div>会员</div>
            </li>
            <li>
                <i class="iconfont">&#xe601;</i>
                <div>统计</div>
            </li>
            <li>
                <i class="iconfont">&#xe604;</i>
                <div>设置</div>
            </li>
        </ul>

    </div>
</template>

<script>
    export default {
        name: 'SideBar'
    }
</script>


<style lang="scss">
    .side-bar {
        color: #fff;
        font-size: 10px;
        height: 100%;
        background-color: #1dbce0;
        float: left;
        width: 5%
    }
    .icon-font {
        font-size: 24px;
    }

    .side-bar ul {
        padding: 0px;
        margin: 0px;
    }

    .side-bar li {
        list-style-type: none;
        text-align: center;
        border-bottom: 1px solid #20a0ff;
        padding: 10px;
    }
</style>

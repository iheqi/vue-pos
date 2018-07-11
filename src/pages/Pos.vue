<template>
    <div class="container"> 
        <el-row>
            <el-col :span="12" class="pos-order">
                <el-tabs>
                    <el-tab-pane label="点餐">
                        <el-table :data="tableData">
                            <el-table-column prop="goodsName" label="商品名称"></el-table-column>
                            <el-table-column prop="count" label="数量"></el-table-column>
                            <el-table-column prop="price" label="金额"></el-table-column>
                            <el-table-column prop="goodsName" label="操作"></el-table-column>
                        </el-table>
                        <div>
                            <el-button type="warning">挂单</el-button>
                            <el-button type="danger">删除</el-button>
                            <el-button type="success">结账</el-button>
                        </div>
                    </el-tab-pane>
                    <el-tab-pane label="挂单">挂单</el-tab-pane>
                    <el-tab-pane label="外卖">外卖</el-tab-pane>

                </el-tabs>
            </el-col>
            <el-col :span="12">
                我是产品栏
            </el-col>
        </el-row>
    </div>       
</template>

<script>
    export default {
        data() {
            return {
                tableData: [{
                    goodsName: '可口可乐',
                    price: 8,
                    count:1
                }, {
                    
                    goodsName: '香辣鸡腿堡',
                    price: 15,
                    count:1
                }, {
                    goodsName: '爱心薯条',
                    price: 8,
                    count:1
                }, {
                    goodsName: '甜筒',
                    price: 8,
                    count:1
                }]
            }
        },
        name: 'Pos',
        mounted() {
        }
    }
</script>

<style lang="scss">
    .container {
        height: 100%;
    }
    el-row {
        height: 100%;
    }
    .pos-order {
        background-color: #f9fafc;
        border-right: 1px solid #c0ccda;
        min-height: 100%;
    }
</style>

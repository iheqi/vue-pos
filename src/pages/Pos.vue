<template>
  <div class="container">
    <el-row>
      <el-col :span="7" class="pos-order" id="order-list">
        <el-tabs>
          <el-tab-pane label="点餐">
            <el-table :data="tableData" border>
              <el-table-column prop="goodsName" label="商品名称"></el-table-column>
              <el-table-column prop="count" label="数量"></el-table-column>
              <el-table-column prop="price" label="金额"></el-table-column>
              <!-- <el-table-column  label="操作" width="100" fixed="right">
                                <template slot-scope="scope">
                                    <el-button type="text" size="small">删除</el-button>
                                    <el-button type="text" size="small">增加</el-button>
                                </template>
                            </el-table-column> -->

              <el-table-column fixed="right" label="操作" width="100">
                <template slot-scope="scope">
                  <el-button type="text" size="small" @click="deleteGood(scope.row)">删除</el-button>
                  <el-button type="text" size="small" @click="addOrderList(scope.row)">增加</el-button>
                </template>
              </el-table-column>
            </el-table>
            <div class="total">
              数量：{{totalCount}} 金额：{{totalMoney}}
            </div>
            <div>
              <el-button type="warning">挂单</el-button>
              <el-button type="danger" @click="delAllGoods">删除</el-button>
              <el-button type="success" @click="checkout">结账</el-button>
            </div>
          </el-tab-pane>
          <el-tab-pane label="挂单">挂单</el-tab-pane>
          <el-tab-pane label="外卖">外卖</el-tab-pane>

        </el-tabs>
      </el-col>
      <el-col :span="17">
        <div class="often-goods">
          <div class="title">常用商品</div>
          <div class="often-goods-list">
            <ul>
              <li v-for="good of oftenGoods" :key="good.goodsId" @click="addOrderList(good)">
                <span>{{good.goodsName}}</span>
                <span class="price">{{good.price}}</span>
              </li>
            </ul>
          </div>
        </div>

        <div class="goods-type">

          <el-tabs>
            <el-tab-pane label="汉堡">
              <div>
                <ul class='cookList'>
                  <li v-for="good of typeGoods" :key="good.goodsId" @click="addOrderList(good)">
                    <span class="foodImg"><img :src="good.goodsImg" width="100%"></span>
                    <span class="foodName">{{good.goodsName}}</span>
                    <span class="foodPrice">{{good.price}}</span>
                  </li>
                </ul>
              </div>
            </el-tab-pane>
            <el-tab-pane label="小食">
              小食
            </el-tab-pane>
            <el-tab-pane label="饮料">
              饮料
            </el-tab-pane>
            <el-tab-pane label="套餐">
              套餐
            </el-tab-pane>

          </el-tabs>
        </div>
      </el-col>
    </el-row>
  </div>
</template>

<script>
export default {
  data() {
    return {
      totalMoney: 0,
      totalCount: 0,
      tableData: [
        {
          goodsName: "可口可乐",
          price: 8,
          count: 1
        },
        {
          goodsName: "香辣鸡腿堡",
          price: 15,
          count: 1
        },
        {
          goodsName: "爱心薯条",
          price: 8,
          count: 1
        },
        {
          goodsName: "甜筒",
          price: 8,
          count: 1
        }
      ],
      oftenGoods: [
        {
          goodsId: 1,
          goodsName: "香辣鸡腿堡",
          price: 18
        },
        {
          goodsId: 2,
          goodsName: "田园鸡腿堡",
          price: 15
        },
        {
          goodsId: 3,
          goodsName: "和风汉堡",
          price: 15
        },
        {
          goodsId: 4,
          goodsName: "快乐全家桶",
          price: 80
        },
        {
          goodsId: 5,
          goodsName: "脆皮炸鸡腿",
          price: 10
        },
        {
          goodsId: 6,
          goodsName: "魔法鸡块",
          price: 20
        },
        {
          goodsId: 7,
          goodsName: "可乐大杯",
          price: 10
        },
        {
          goodsId: 8,
          goodsName: "雪顶咖啡",
          price: 18
        },
        {
          goodsId: 9,
          goodsName: "大块鸡米花",
          price: 15
        },
        {
          goodsId: 20,
          goodsName: "香脆鸡柳",
          price: 17
        }
      ],
      typeGoods: [
        {
          goodsId: 1,
          goodsImg: "http://7xjyw1.com1.z0.glb.clouddn.com/pos001.jpg",
          goodsName: "香辣鸡腿堡",
          price: 18
        },
        {
          goodsId: 2,
          goodsImg: "http://7xjyw1.com1.z0.glb.clouddn.com/pos002.jpg",
          goodsName: "田园鸡腿堡",
          price: 15
        },
        {
          goodsId: 3,
          goodsImg: "http://7xjyw1.com1.z0.glb.clouddn.com/pos004.jpg",
          goodsName: "和风汉堡",
          price: 15
        },
        {
          goodsId: 4,
          goodsImg: "http://7xjyw1.com1.z0.glb.clouddn.com/pos003.jpg",
          goodsName: "快乐全家桶",
          price: 80
        },
        {
          goodsId: 5,
          goodsImg: "http://7xjyw1.com1.z0.glb.clouddn.com/pos003.jpg",
          goodsName: "脆皮炸鸡腿",
          price: 10
        },
        {
          goodsId: 6,
          goodsImg: "http://7xjyw1.com1.z0.glb.clouddn.com/pos004.jpg",
          goodsName: "魔法鸡块",
          price: 20
        },
        {
          goodsId: 7,
          goodsImg: "http://7xjyw1.com1.z0.glb.clouddn.com/pos001.jpg",
          goodsName: "可乐大杯",
          price: 10
        },
        {
          goodsId: 8,
          goodsImg: "http://7xjyw1.com1.z0.glb.clouddn.com/pos003.jpg",
          goodsName: "雪顶咖啡",
          price: 18
        },
        {
          goodsId: 9,
          goodsImg: "http://7xjyw1.com1.z0.glb.clouddn.com/pos002.jpg",
          goodsName: "大块鸡米花",
          price: 15
        },
        {
          goodsId: 20,
          goodsImg: "http://7xjyw1.com1.z0.glb.clouddn.com/pos002.jpg",
          goodsName: "香脆鸡柳",
          price: 17
        }
      ]
    };
  },
  name: "Pos",
  mounted() {
    var orderHeight = document.body.clientHeight;
    document.getElementById("order-list").style.height = orderHeight + "px";
    this.getAllMoney()
  },
  methods: {
    addOrderList(goods) {
      this.totalCount = 0;
      this.totalMoney = 0;
      let isHave = false;
      for (let i = 0; i < this.tableData.length; i++) {
        console.log(this.tableData[i].goodsId);
        if (this.tableData[i].goodsId == goods.goodsId) {
          isHave = true; //存在
        }
      }
      if (isHave) {
        let arr = this.tableData.filter(o => o.goodsId == goods.goodsId);
        arr[0].count++;
      } else {
        let newGoods = {
          goodsId: goods.goodsId,
          goodsName: goods.goodsName,
          price: goods.price,
          count: 1
        };
        this.tableData.push(newGoods);
      }

      this.tableData.forEach(element => {
        this.totalCount += element.count;
        this.totalMoney = this.totalMoney + element.price * element.count;
      });
    },

    deleteGood(goods) {
      this.tableData = this.tableData.filter(item => {
        return item.goodsName != goods.goodsName
      });
      this.getAllMoney()
    },

    delAllGoods() {
      this.tableData = [];
      this.totalCount = 0;
      this.totalMoney = 0;
    },

    getAllMoney() {
      this.totalCount = 0;
      this.totalMoney = 0;
      if (this.tableData) {
        this.tableData.forEach((element) => {
          this.totalCount += element.count;
          this.totalMoney = this.totalMoney + (element.price * element.count);
        });
      }

    },
    checkout() {
      if (this.totalCount != 0) {
        this.tableData = [];
        this.totalCount = 0;
        this.totalMoney = 0;
        this.$message({
          message: '结账成功，感谢你又为店里出了一份力!',
          type: 'success'
        });

      } else {
        this.$message.error('不能空结。老板了解你急切的心情！');
      }
    }
  }
};
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
  height: 100%;
}
el-table {
  width: 100%;
}

.title {
  height: 20px;
  border-bottom: 1px solid #d3dce6;
  background-color: #f9fafc;
  text-align: left;
  padding: 10px;
}

.often-goods-list ul li {
  float: left;
  border: 1px solid #e5e9f2;
  padding: 10px;
  margin: 10px;
  background-color: #fff;
}

.price {
  color: #58b7ff;
}

.price::before {
  content: " $";
}

.goods-type {
  clear: both;
}

.cookList li {
  list-style: none;
  width: 23%;
  border: 1px solid #e5e9f2;
  height: auot;
  overflow: hidden;
  background-color: #fff;
  padding: 2px;
  float: left;
  margin: 2px;
  cursor: pointer;
}
.cookList li span {
  display: block;
  float: left;
}
.foodImg {
  width: 40%;
}
.foodName {
  font-size: 16px;
  padding-left: 10px;
  color: brown;
}
.foodPrice {
  font-size: 16px;
  padding-left: 10px;
  padding-top: 10px;
}

.total {
  background-color: #fff;
  padding: 10px;
  padding: 10px;
}
</style>

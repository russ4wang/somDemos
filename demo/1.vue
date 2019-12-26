<template>
  <div class="demo">
    <van-action-sheet v-model="show">
      <div class="sheet-guige">
        <div class="sheet-guige-price">
          <div class="sheet-guige-price-img">
            <img :src="pic" alt srcset />
          </div>
          <div class="sheet-guige-price-text">
            <i class="chinese">￥</i>
          </div>
          <div class="sheet-guige-price-text1">
            <p>
              已选：
              <span v-for="(value,key) in selectedSpecification" :key="key">{{value}},</span>
            </p>
          </div>
          <div class="sheet-guige-price-shut" @click="guige">
            <img src="../../assets/img/close.png" alt srcset />
          </div>
        </div>
        <div
          class="sheet-guige-specification clearfloat"
          v-for="(item,key) in specification "
          :key="key"
        >
          <p>{{item.name }}</p>
          <div
            class="sheet-guige-specification-pth"
            :v-if=" item.pmsGoodsAttributeValueVoList "
            v-for="(items,keys) in item.pmsGoodsAttributeValueVoList "
            :key="keys"
            @click="specificationBtn(item,key,items,keys,items.value)"
          >
            <div
              class="sheet-guige-specification-btn"
              :class="selectedSpecification[key]==items.value?'gaipian':''"
            >
              <div class="sheet-guige-specification-btn-w">{{items.value}}</div>
            </div>
          </div>
        </div>
        <div class="sheet-guige-specification-quantity-purchase">
          <p>购买数量</p>
          <div class="purchase-bujinqi">
            <van-stepper v-model="specificationValue" integer />
          </div>
        </div>
        <div class="sheet-guige-purchase">
          <div class="sheet-guige-purchase-gouw" @click="shopping">加入购物车</div>
          <div class="sheet-guige-purchase-lij" @click="purchase">立即购买</div>
        </div>
      </div>
    </van-action-sheet>
  </div>
</template>
<script>
export default {
  data() {
    return {
      show: false,
      specificationName: "",
      specification: null,
      selectedSpecification: [],
      specification: [
        {
          id: 39,
          name: "尺码",
          pmsGoodsAttributeValueVoList: [
            { id: 7, pmsGoodsVo: "", value: "L" },
            { id: 8, pmsGoodsVo: "", value: "XL" }
          ],
          type: 0
        },
        {
          id: 40,
          name: "颜色",
          pmsGoodsAttributeValueVoList: [
            { id: 9, pmsGoodsVo: "", value: "黄色" },
            { id: 10, pmsGoodsVo: "", value: "蓝色" }
          ],
          type: 0
        }
      ]
    };
  },
  methods: {
    guige() {
      this.show = !this.show;
    },
    specificationBtn(item, key, items, keys, a) {
      this.selectedSpecification[key] = items.value;
      this.$forceUpdate();
    }
  }
};
</script>
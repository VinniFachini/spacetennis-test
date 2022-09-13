<template>
  <div class="item">
    <img :src="itemInfo.img" />
    <div class="info">
      <div class="item-name">{{ itemInfo.name }}</div>
      <div class="item-price">R$ {{ itemInfo.price | money }}</div>
      <button @click="buyProducts(itemInfo.id, itemInfo.image, itemInfo.name, itemInfo.price, itemInfo.size)" class="btn">Comprar</button>
    </div>
  </div>
</template>

<script>
export default {
  props: ["itemInfo"],
  methods: {
    buyProducts(itemId, itemImg, itemName, itemPrice, itemSize) {
      const list = this.$root.$refs.carrinho.cartItems
      if(list.some(data => data.id !== itemId )) {
        this.$root.$refs.carrinho.cartItems.push({
            id: itemId,
            img: itemImg,
            name: itemName, 
            size: itemSize,
            price: itemPrice,
          })
      }else {
        return
      }
    }
  },
  filters: {
    money: function (value) {
      if (!value instanceof Number) {
        return "";
      } else {
        return String((Math.round(value * 100) / 100).toFixed(2)).replace(
          ".",
          ","
        );
      }
    },
  },
};
</script>

<style scoped>
.item {
  display: flex;
  flex-direction: column;
  align-items: center;
  flex-basis: 300px;
}
.item img {
  width: 100%;
  max-width: 300px;
}
.item-name, .item-price {
  color: #002c5b;
  font-size: 14px;
  letter-spacing: 0.5px;
  font-weight: 600;
  text-transform: uppercase;
  text-align: center;
}

.item-price {
  font-size: 14px;
}

.info {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.btn {
  color: white;
  background: #222222;
  padding: 8px 15px;
  letter-spacing: 0.5px;
  text-transform: uppercase;
  font-size: 12px;
  font-weight: 600;
  text-align: center;
  cursor: pointer;
  transition: all 0.3s;
  border:none;
  outline:none;
  width: 50%;
}

.btn:hover {
  color: #222222;
  background-color: #ccc;
}
</style>
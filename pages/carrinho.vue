<template>
  <div class="container">
    <Header />
    <main>
      <div class="box">
        <div class="items">
          <div class="props-row">
            <span>produto</span>
            <span>detalhe</span>
            <span>qtd</span>
            <span>total</span>
          </div>
          <CartItem
            ref="child"
            @deletedProduct="deleteItem"
            @ammountUpdated="updateAmmount"
            @componentCreated="created"
            v-for="item in cartItems"
            :key="item.id"
            :itemData="item"
          />
          <div class="action-group">
            <div class="keep-buying btn">continuar comprando</div>
            <div class="second">
              <div @click="deleteEveryItem" class="clear-btn btn">
                limpar carrinho
              </div>
              <div class="share-btn btn">compartilhar</div>
            </div>
          </div>
        </div>
        <div class="final-price">
          <div class="subtotal-group">
            <div class="title">subtotal</div>
            <div class="subtotal">R$ {{ totalPrice | money }}</div>
          </div>
          <div class="frete">
            <div class="form-group">
              <the-mask
                class="form-input"
                mask="#####-###"
                value=""
                type="tel"
                :masked="true"
                placeholder="CEP"
              />
              <input type="button" value="CALCULAR FRETE" />
            </div>
            <div class="fretes">Fretes:</div>
          </div>
          <div class="total">
            <span>total</span>
            <div class="total-price">R$ {{ applyDiscount | money }}</div>
          </div>
          <div class="form-group-cupom">
            <the-mask
              ref="discount"
              class="form-input"
              mask="XXXXX"
              value=""
              type="tel"
              :masked="true"
              placeholder="Cupom de desconto"
            />
            <input @click="getDiscount" type="button" value="USAR" />
          </div>
          <input type="button" value="FINALIZAR COMPRA" />
        </div>
      </div>
      <div class="see-more-products">
        <h2>Aproveite e leve também</h2>
        <div class="items">
          <Item
            v-for="item in suggestionItems"
            :key="item.id"
            :itemInfo="item"
          />
        </div>
      </div>
    </main>
    <Footer />
  </div>
</template>

<script>
import { TheMask } from "vue-the-mask";
import Item from "~/components/Item.vue";
export default {
  data() {
    return {
      items: [],
      cartItems: [],
      suggestionItems: [],
      discount: 0
    };
  },
  methods: {
    getDiscount(){
      if(this.$refs.discount.display <= 35) {
        this.discount = this.$refs.discount.display / 100;
      } else {return}
    },
    deleteEveryItem() {
      if (this.$refs.child.length >= 1) {
        this.items = [];
        this.$refs.child.forEach((item) => {
          item.$destroy();
          item.$el.parentNode.removeChild(item.$el);
        });
      }
    },
    created(variable) {
      this.items.push(variable);
    },
    updateAmmount(variable) {
      this.items.map((item) => {
        if (item.itemId == variable.id) {
          item.ammount = variable.ammount;
        }
      });
    },
    deleteItem(variable) {
      this.items.map((item, index) => {
        if (item.itemId == variable.id) {
          this.items.splice(index, 1);
        }
      });
    },
  },
  computed: {
    applyDiscount() {
      return this.totalPrice - (this.totalPrice * this.discount)
    },
    totalPrice() {
      return this.items
        .map((item) => item.ammount * item.itemPrice)
        .reduce((a, b) => a + b, 0);
    },
  },
  head() {
    return {
      title: "Carrinho: Loja de tênis online - Comprar agora",
    };
  },
  async fetch() {
    this.cartItems = await fetch(
      "https://spacetennis-express-api.vercel.app/api/products?max=2"
    ).then((res) => res.json());
    this.suggestionItems = await fetch(
      "https://spacetennis-express-api.vercel.app/api/products?max=4"
    ).then((res) => res.json());
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
  components: { Item, TheMask },
};
</script>

<style scoped>
main {
  width: 100%;
  max-width: 1280px;
}
.container {
  display: flex;
  flex-direction: column;
  align-items: center;
  overflow: hidden;
}
.box {
  margin-top: 80px;
  display: flex;
  width: 100%;
  justify-content: space-between;
  gap: 30px;
}

.props-row {
  display: flex;
  padding-bottom: 16px;
  border-bottom: 1px solid #ccc;
  width: 100%;
}

.props-row > span {
  color: #222222;
  font-size: 12px;
  letter-spacing: 0.5px;
  font-weight: 400;
  text-transform: uppercase;
}

.props-row > span:nth-of-type(1) {
  flex-grow: 1;
  margin-left: 5px;
}
.props-row > span:nth-of-type(2) {
  flex-grow: 4;
}
.props-row > span:nth-of-type(3) {
  flex-grow: 2;
}
.props-row > span:nth-of-type(4) {
  margin-right: 5px;
}

.items {
  display: flex;
  flex-direction: column;
  flex: 2;
}
.action-group {
  display: flex;
  justify-content: space-between;
  margin-top: 25px;
}

.action-group .btn {
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
}

.action-group .btn:hover {
  color: white;
  background: #222222;
  color: #222222;
  background-color: #ccc;
}

.action-group > .second {
  display: flex;
  gap: 20px;
}

.final-price {
  display: flex;
  flex-direction: column;
}

.subtotal-group {
  display: flex;
  align-items: center;
  justify-content: space-between;
  border-bottom: 1px solid #ccc;
  width: 100%;
}

.subtotal-group > .title {
  color: #222222;
  font-size: 12px;
  letter-spacing: 0.5px;
  font-weight: 400;
  text-transform: uppercase;
  height: 100%;
  margin-left: 5px;
}

.subtotal-group > .subtotal {
  color: #002c5b;
  font-size: 18px;
  font-weight: 400;
  letter-spacing: 0.5px;
  margin-bottom: 9px;
  height: 100%;
  margin-right: 15px;
}

.blocked {
  background-color: tomato;
}

.frete {
  display: flex;
  flex-direction: column;
  border-bottom: 1px solid #ccc;
}

.frete > .form-group {
  display: flex;
  margin-top: 10px;
  padding: 0 2px;
}

.frete .form-group .form-input {
  border: 1px solid #ccc;
  padding: 10px;
}

.frete .form-group input[type="button"] {
  color: white;
  background: #222222;
  padding: 8px 15px;
  letter-spacing: 0.5px;
  text-transform: uppercase;
  font-size: 10px;
  font-weight: 600;
  text-align: center;
  cursor: pointer;
  outline: none;
  transition: all 0.3s;
  border: none;
}

.frete .form-group input[type="button"]:hover {
  background-color: #ccc;
  color: #222;
}

.frete .fretes {
  color: #222222;
  font-size: 11px;
  letter-spacing: 0.5px;
  font-weight: 400;
  text-transform: uppercase;
  height: 100%;
  margin-left: 5px;
  margin-block: 15px;
}

.final-price .total {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding-block: 5px;
  border-bottom: 1px solid #ccc;
}

.final-price .total span {
  color: #222222;
  font-size: 11px;
  letter-spacing: 0.5px;
  font-weight: 400;
  text-transform: uppercase;
  margin-left: 5px;
}

.final-price .total .total-price {
  color: #002c5b;
  font-size: 24px;
  letter-spacing: 0.5px;
  font-weight: 700;
  margin-right: 15px;
}

.form-group-cupom {
  display: flex;
  align-items: center;
  padding: 0 2px;
  padding-block: 10px;
  border-bottom: 1px solid #ccc;
}
.form-group-cupom > .form-input {
  border: 1px solid #ccc;
  padding: 10px;
  flex-grow: 4;
}

.form-group-cupom > input[type="button"] {
  color: white;
  background: #222222;
  padding: 8px 15px;
  letter-spacing: 0.5px;
  text-transform: uppercase;
  font-size: 10px;
  font-weight: 600;
  text-align: center;
  cursor: pointer;
  outline: none;
  transition: all 0.3s;
  border: none;
  flex-grow: 2;
  height: 100%;
}

.form-group-cupom input[type="button"]:hover {
  background-color: #ccc;
  color: #222;
}

.final-price > input[type="button"] {
  border-radius: 4px;
  border: none;
  background-color: #5bb85a;
  color: white;
  font-size: 20px;
  letter-spacing: 0.5px;
  padding: 10px;
  font-weight: 400;
  text-align: center;
  margin-top: 10px;
  cursor: pointer;
  transition: all 0.3s;
  margin-bottom: 10px;
}

.final-price > input[type="button"]:hover {
  background-color: #32a730;
}

.see-more-products {
  display: flex;
  align-items: center;
  justify-content: center;
  margin-top: 30px;
  flex-direction: column;
}

.see-more-products h2 {
  font-family: Syncopate, sans-serif;
  font-size: 20px;
  letter-spacing: 0.5px;
  font-weight: bold;
  color: #002c5b;
}

.see-more-products > .items {
  display: flex;
  width: 100%;
  flex-direction: row;
  align-items: center;
  justify-content: space-between;
  gap: 27px;
}
@media screen and (max-width: 1366px) {
  .container {
    padding: 0 2%;
  }
  .form-group-cupom > input[type="button"] {
    height: 100%;
    padding-block: 13px;
  }
}

@media screen and (max-width: 991px) {
  .box {
    flex-direction: column;
  }
  .container {
    padding: 0 8%;
  }
  .frete {
    margin-bottom: 10px;
  }
  .fretes {
    display: none;
  }
  .frete > .form-group {
    margin-bottom: 10px;
  }
  .total {
    margin-top: -10px;
  }
  .see-more-products h2 {
    text-align: center;
  }
  .see-more-products > .items {
    flex-direction: column !important;
  }
}

@media screen and (max-width: 768px) {
  .props-row > span {
    display: none;
  }
}

@media screen and (max-width: 605px) {
  .action-group,
  .action-group .second {
    flex-direction: column;
    gap: 10px;
  }
}
</style>


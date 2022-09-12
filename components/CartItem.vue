<template>
  <div class="products">
    <div class="product-card">
      <div class="image">
        <img :src="itemData.img" />
      </div>
      <div class="product-info">
        <div class="product-name">
          {{ itemData.name }}
        </div>
        <div class="product-size">
          TAMANHO: <strong>{{ itemData.size }}</strong>
        </div>
        <div class="product-price">por R$ {{ itemData.price | money }}</div>
        <div class="message">
          <label for="message-text">
            <span>EMBALAGEM PARA PRESENTE.</span>
            <input type="checkbox" />
          </label>
        </div>
      </div>
      <div class="actions">
        <div class="delete-item" @click="softDeleteProduct">
          <svg
            xmlns="http://www.w3.org/2000/svg"
            width="24"
            height="24"
            style="fill: #ccc; transform: ; msfilter: "
          >
            <path
              d="M5 20a2 2 0 0 0 2 2h10a2 2 0 0 0 2-2V8h2V6h-4V4a2 2 0 0 0-2-2H9a2 2 0 0 0-2 2v2H3v2h2zM9 4h6v2H9zM8 8h9v12H7V8z"
            ></path>
            <path d="M9 10h2v8H9zm4 0h2v8h-2z"></path>
          </svg>
        </div>
        <div class="increase-decrease">
          <button @click="decrease">
            <svg
              xmlns="http://www.w3.org/2000/svg"
              width="24"
              height="24"
              style="fill: rgba(0, 0, 0, 1); transform: ; msfilter: "
            >
              <path d="M5 11h14v2H5z"></path>
            </svg>
          </button>
          <div class="ammount">{{ ammount }}</div>
          <button @click="increase">
            <svg
              xmlns="http://www.w3.org/2000/svg"
              width="24"
              height="24"
              style="fill: rgba(0, 0, 0, 1); transform: ; msfilter: "
            >
              <path d="M19 11h-6V5h-2v6H5v2h6v6h2v-6h6z"></path>
            </svg>
          </button>
        </div>
      </div>
      <div class="total-price-item">
        R$ {{ (itemData.price * ammount) | money }}
      </div>
    </div>
  </div>
</template>

<script>
export default {
  methods: {
    decrease: function () {
      if (this.ammount > 1) {
        this.ammount--;
        this.$emit("ammountUpdated", {
          id: this.$props.itemData.id,
          ammount: this.ammount,
        });
      } else {
        this.softDeleteProduct();
      }
    },
    increase: function () {
      this.ammount++;
      this.$emit("ammountUpdated", {
        id: this.$props.itemData.id,
        ammount: this.ammount,
      });
    },
    softDeleteProduct: function () {
      this.$emit("deletedProduct", this.$props.itemData);
      this.DeleteProduct()  
    },
    DeleteProduct: function () {
      this.$destroy();
      this.$el.parentNode.removeChild(this.$el);
    }
  },
  props: ["itemData"],
  data() {
    return {
      ammount: 1,
    };
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
  mounted() {
    this.$emit("componentCreated", {
      itemId: this.$props.itemData.id,
      itemPrice: this.$props.itemData.price,
      ammount: this.ammount,
    });
  },
};
</script>

<style>
.products {
  display: flex;
  flex-direction: column;
  flex-grow: 30;
}
.product-card {
  display: flex;
  border-bottom: 1px solid #ccc;
  justify-content: space-between;
}

.product-card > .image > img {
  width: 100%;
  max-width: 100px;
  padding-top: 50px;
  flex-grow: 1;
  margin-left: 5px;
}

.product-card .product-info {
  display: flex;
  flex-direction: column;
  padding: 25px;
  justify-content: space-evenly;
  flex-grow: 3;
  margin-left: 20px;
}

.product-card .product-info > .product-name,
.product-card .product-info > .product-size {
  color: #002c5b;
  font-size: 12px;
  letter-spacing: 0.5px;
  text-transform: uppercase;
  font-weight: 400;
}

.product-card .product-info > .product-name {
  max-width: 275px;
}

.product-card .product-info > .product-price {
  color: #002c5b;
  font-size: 14px;
  letter-spacing: 0.5px;
  font-weight: 700;
  margin: 15px 0;
}

.product-card .product-info > .message > label {
  display: flex;
  align-items: center;
}

.product-card .product-info > .message label > span {
  color: #002c5b;
  font-size: 11px;
  order: 2;
  margin-left: 10px;
}
.product-card .product-info > .message label > input {
  transform: scale(1.5);
}

.product-card .actions {
  display: flex;
  align-items: center;
  flex-grow: 3;
}

.product-card .actions .increase-decrease {
  display: flex;
  height: 25px;
  margin-left: 20px;
}

.product-card .actions .increase-decrease div {
  width: 25px;
  height: 25px;
  font-size: 14px;
  line-height: 25px;
  text-align: center;
  border-top: 1px solid #ccc;
  border-bottom: 1px solid #ccc;
}
.product-card .actions .increase-decrease button {
  border: 1px solid #ccc;
  background-color: transparent;
}

.product-card .actions .increase-decrease button svg {
  transform: scale(0.5);
}

.product-card .total-price-item {
  flex-grow: 1;
  align-self: center;
  color: #002c5b;
  font-size: 17px;
  letter-spacing: 0.5px;
  font-weight: 700;
  text-transform: uppercase;
}
@media screen and (max-width: 1366px) {
  .product-card .product-info {
    flex-basis: 300px;
  }
  .product-card .actions {
    flex-basis: 150px;
  }
  .product-card .actions .increase-decrease {
    margin-left: 5px;
  }
  .product-card .total-price-item {
    flex-basis: 100px;
  }
}

@media screen and (max-width: 684px) {
  .product-card {
    flex-direction: column;
    padding-bottom: 25px;
  }
  .product-card .image {
    width: 100%;
    display: flex;
    align-items: center;
    justify-content: center;
    margin-top: -50px;
  }
  .product-card .image img {
    max-width: 200px;
  }

  .product-info {
    justify-content: center !important;
    margin-left: 0 !important;
    width: 100%;
    height: 100% !important;
    max-height: 150px !important;
    flex-grow: 1 !important;
  }
  .product-info .product-name,
  .product-info .product-size,
  .product-info .product-price {
    text-align: center;
  }
  .product-info .message {
    align-self: center;
  }
  .actions {
    flex-grow: 1 !important;
    justify-content: center;
    flex-direction: column;
    height: 100%;
    max-height: 70px;
    margin-top: -20px;
  }
  .total-price-item {
    width: 100%;
    text-align: center;
    font-size: 24px;
    height: 100%;
    max-height: 25px;
    flex-basis: 0 !important;
  }
}
</style>
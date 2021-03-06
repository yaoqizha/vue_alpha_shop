<template>
  <div class="shopping-cart__panel">
    <div id="shopping-cart-container">
      <h4 class="shopping-cart__panel--title">購物籃</h4>
      <div class="shopping-cart__panel--items">
        <div
          v-for="product in products"
          :key="product.id"
          class="shopping-cart__panel--item"
        >
          <div class="img-wrapper">
            <img :src="product.image" class="shopping-cart-image" />
          </div>
          <div class="shopping-cart__panel--item-right">
            <div class="cart-item-title">{{ product.name }}</div>
            <div id="product1" class="cart-item-buttons-wrapper">
              <div class="cart-item-button1" @click="addAmount(product)"></div>
              <div class="cart-item-number">{{ product.amount }}</div>
              <div
                class="cart-item-button2"
                @click="minusAmount(product)"
              ></div>
            </div>
            <div class="cart-item-price">{{ product.totalPrice }}</div>
          </div>
        </div>
        <div class="shipping-fee-wrapper">
          <div class="shipping-fee-title">運費</div>
          <div class="shipping-fee-amount">{{ shippingFee? `$${shippingFee}`: "免費" }}</div>
        </div>
        <div class="total-fee-wrapper">
          <div class="total-fee-title">小計</div>
          <div class="total-fee-amount">{{ finalPrice }}</div>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  data() {
    return {
      products: [
        {
          id: 1,
          name: "破壞補釘修身牛仔褲",
          image: require("../../public/product1@1x.png"),
          amount: 1,
          price: 3999,
          totalPrice: "$3,999",
        },
        {
          id: 2,
          name: "刷色直筒牛仔褲",
          image: require("../../public/product2@1x.png"),
          amount: 1,
          price: 1299,
          totalPrice: "$1,299",
        },
      ],
    };
  },
  props: {
    shippingFee: Number,
  },
  computed: {
    finalPrice() {
      const price =
        this.products.reduce((acc, item) => acc + item.price * item.amount, 0) +
        this.shippingFee;

      return new Intl.NumberFormat("en-US", {
        style: "currency",
        currency: "USD",
        maximumFractionDigits: 0,
      }).format(price);
    },
  },
  methods: {
    addAmount(product) {
      product.amount += 1;
      product.totalPrice = new Intl.NumberFormat("en-US", {
        style: "currency",
        currency: "USD",
        maximumFractionDigits: 0,
      }).format(product.amount * product.price);
    },
    minusAmount(product) {
      if (product.amount > 0) {
        product.amount -= 1;
        product.totalPrice = new Intl.NumberFormat("en-US", {
          style: "currency",
          currency: "USD",
          maximumFractionDigits: 0,
        }).format(product.amount * product.price);
      }
    },
  },
};
</script>

<style lang="scss" scoped>
%cart-button-style {
  width: 26px;
  height: 27px;
  position: relative;
  z-index: 0;
  border-radius: 50%;
  background-color: var(--cart-button);
}

%cart-button-content {
  width: 100%;
  height: 100%;
  line-height: 100%;
  position: absolute;
  z-index: -1;
  text-align: center;
  color: black;
  font-weight: 500;
  font-size: 24px;
}

.shopping-cart__panel {
  grid-column: 4/5;
  padding: 16px 24px;
  border: 1px solid var(--pale-grey);
  border-radius: 8px;
  padding: 16px;
  background-color: var(--shoppingcart-bg);

  &--title {
    display: block;
    margin-bottom: 32px;
  }

  &--items {
    width: 100%;
  }

  &--item {
    width: 100%;
    height: 102px;
    margin-bottom: 32px;
    display: flex;
    flex-flow: row nowrap;
    justify-content: space-between;

    .img-wrapper {
      height: 100%;
      width: 100px;
    }

    .shopping-cart-image {
      object-fit: cover;
      border-radius: 5px;
    }

    &-right {
      height: 100%;
      display: flex;
      flex-flow: column nowrap;
      align-items: flex-end;

      .cart-item-title {
        margin-bottom: 16px;
        font-size: 16px;
        font-weight: 400;
        line-height: 24px;
      }

      .cart-item-buttons-wrapper {
        height: 27px;
        width: 116px;
        margin-bottom: 16px;
        display: flex;
        align-items: center;
        justify-content: space-between;

        .cart-item-button1 {
          @extend %cart-button-style;

          &::after {
            content: "+";
            @extend %cart-button-content;
          }
        }

        .cart-item-button2 {
          @extend %cart-button-style;

          &::after {
            content: "–";
            @extend %cart-button-content;
          }
        }

        .cart-item-number {
          line-height: 17px;
          font-weight: 500;
          font-size: 14px;
        }
      }

      .cart-item-price {
        line-height: 22px;
        font-weight: 700;
        font-size: 16px;
      }
    }
  }

  .shipping-fee-wrapper {
    width: 100%;
    height: 37px;
    border-top: 1px solid #f0f0f5;
    margin-bottom: 32px;
    display: flex;
    justify-content: space-between;
    align-items: flex-end;

    .shipping-fee-title {
      line-height: 20px;
      font-weight: 400;
      font-size: 14px;
      color: var(--main-fc);
    }

    .shipping-fee-amount {
      line-height: 17px;
      font-weight: 700;
      font-size: 14px;
      color: var(--main-fc);
    }
  }

  .total-fee-wrapper {
    width: 100%;
    height: 37px;
    border-top: 1px solid #f0f0f5;
    margin-bottom: 32px;
    display: flex;
    justify-content: space-between;
    align-items: flex-end;

    .total-fee-title {
      line-height: 20px;
      font-weight: 400;
      font-size: 14px;
      color: var(--main-fc);
    }

    .total-fee-amount {
      line-height: 17px;
      font-weight: 700;
      font-size: 14px;
      color: var(--main-fc);
    }
  }
}
</style>
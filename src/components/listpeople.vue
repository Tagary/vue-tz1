<template >
  <div class="main-info">
    <div class="main-info__title">People</div>
    <div class="main-info__sort">
      <button
        ref="sortmenu"
        @click="popupVisible = !popupVisible"
        class="sort-by"
      >
        Sort By:
      </button>
      <transition name="popupmenu">
        <div
          class="popup"
          ref="popuphave"
          @mouseleave="changePopup"
          v-if="popupVisible"
        >
          <div @click="allSort">All</div>
          <div @click="sortMale">Male</div>
          <div @click="sortFemale">Female</div>
        </div>
      </transition>
    </div>
    <div class="container-card">
      <div class="cards" v-for="data in sortProducts" :key="data.id">
        <div class="cards-user">
          <div class="card-user_options">⋮</div>
          <div class="cart-user_center">
            <img class="user-ava" :src="data.image" />
          </div>
          <div class="cart-user_center">
            {{ data.firstname }} {{ data.lastname }}
          </div>
          <div class="cart-user_center cart-user_email">{{ data.email }}</div>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
import axios from 'axios';
export default {
    
  props: {
    sortProduct: {
      type: Array,
      requred: false,
    },
    
  },
  data() {
    return {
      popupVisible: false,
      checkOutSide: false,
      datas: [],
      sort: [],
    };
  },
      created() {
        axios.get('https://fakerapi.it/api/v1/persons?_quantity=10').then(resp=> {this.datas = resp.data.data});
    },
  methods: {
    sortMale: function () {
      let thisNf = this;
      thisNf.sort = [];
      this.datas.map((item) => {
        if (item.gender == "male") {
          thisNf.sort.push(item);
        }
      });
    },

    sortFemale: function () {
      let thisNf = this;
      thisNf.sort = [];
      this.datas.map((item) => {
        if (item.gender == "female") {
          thisNf.sort.push(item);
        }
      });
    },
    allSort: function () {
      let thisNf = this;
      thisNf.sort = [];
      thisNf.sort = thisNf.datas;
    },
    changePopup: function () {
      let thisNf = this;
      document.addEventListener("click", function (item) {
        if (item.target !== thisNf.$refs.popuphave) {
          thisNf.popupVisible = false;
        }
        if (item.target === thisNf.$refs.sortmenu) {
          thisNf.popupVisible = true;
        }
      });
    },
    sendDataInfo() {
      this.$emit('sendData', this.datas)
    },

  },
      computed: {
        sortProducts()  {
            if (this.sort.length) {
                return this.sort
            } else {
                return this.datas
            }
        }

        },
};
</script>
<style scoped>
.main-info {
  width: 80%;
  padding: 20px;
}

.popup {
  position: absolute;
  top: 0;
  left: 60px;
  background-color: rgb(214, 207, 207);
  padding: 10px;
}

        .user-ava {
        border-radius: 50%;
        width: 50px;
        height: 50px;
    }


.popup div {
  cursor: pointer;
}
.popup div:nth-child(1) {
  margin-bottom: 10px;
}
.popup div:nth-child(2) {
  margin-bottom: 10px;
}

.popupmenu-enter-active,
.popupmenu-leave-active {
  transition: ease-in-out 0.5s;
}
.popupmenu-enter,
.popupmenu-leave-to {
  transform: translateX(100px);
  opacity: 0;
}

.container-card {
  display: flex;
  flex-wrap: wrap;
  margin-top: 70px;
}

.cards-user {
  width: 200px;
  height: 300px;
  margin: 20px;
  padding: 20px;
  border-radius: 20px;
  border: 1px solid gray;
}

.card-user_options {
  display: flex;
  justify-content: end;
  margin-bottom: 30px;
}
.cart-user_email {
  margin-top: 10px;
  font-size: 14px;
  word-wrap: break-word;
}

.main-info__title {
  font-size: 25px;
  margin-bottom: 10px;
  font-weight: bold;
}

.main-info__sort {
    position: relative;
}
    .sort-by {
        border: none;
        cursor: pointer;
        font-weight: bold;
        background: #000;
        color: #fff;
        padding: 3px;
        border-radius: 10px;
    }



    .cart-user_center {
        text-align: center;
    }

</style>
    

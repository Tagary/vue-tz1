<template >
  <div class="wrapper">
    <div class="container">
      <section class="left-colum">
        <div class="container-logo">
          <div class="logo">
            <img src="../public/images/imglogo.svg" alt="" />
          </div>
          <div>
            <img src="../public/images/arrowdown.svg" alt="" />
          </div>
        </div>
        <div class="button-left">
          <button class="button-left_request">Request for</button>
        </div>
        <ul class="menu">
          <li><img src="../public/images/dashboard.svg" alt="" /> Dashbord</li>
          <li><img src="../public/images/people.svg" alt="" /> People</li>
          <li><img src="../public/images/handmoney.svg" alt="" /> Finances</li>
          <li>
            <img src="../public/images/statistics.svg" alt="" /> Statistics
          </li>
          <li><img src="../public/images/documents.svg" alt="" /> Documents</li>
          <li><img src="../public/images/calendar.svg" alt="" />Calendar</li>
        </ul>
        <div class="support">
          <img src="../public/images/support.svg" alt="" />
          Support
        </div>
        <div class="button-off">
          <img src="../public/images/buttonon.svg" alt="" />
        </div>
      </section>
      <section class="right-colum">
        <nav class="nav-bar">
          <div class="nav-bar__input">
            <input type="text" />
          </div>
          <div class="nav-bar__info">
            <div class="data" @load="loadTime">{{ daysnow }}</div>
            <div class="alert">
              <img src="../public/images/alert.svg" alt="" />
            </div>
            <div class="user-name">
              Cristo Parino
              <img
                class="user-ava_main"
                src="../public/images/images.jpg"
                alt=""
              />
              <img src="../public/images/arrowdown.svg" alt="" />
            </div>
          </div>
        </nav>
        <div class="main">
          <list-people :sortProduct="sortProduct" @sendData="showData" />
          <div class="main-stat">
            <p class="main-stat_select">Selected</p>
            <h1>Design Team</h1>
            <div class="container-stats">
              <div class="stats-option_img">
                <img src="../public/images/settings.svg" alt="" />
              </div>
              <div class="stats-time">
                <span class="stats-time_content">
                  Time Log
                  <span>74%</span>
                </span>
              </div>
              <h2>Projects</h2>
              <div>
                <div>
                  <div>
                    TOTAL
                    <span>148</span>
                  </div>
                  <div>
                    COMPLITED
                    <span>56</span>
                  </div>
                </div>
                <div>
                  <div>
                    IN PROGRESS
                    <span>76</span>
                  </div>
                  <div>
                    WAITING
                    <span> 16 </span>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </section>
    </div>
  </div>
</template>
<script>
import ListPeople from "./components/ListPeople.vue";

export default {
  components: {
    ListPeople,
  },

  data() {
    return {
      datas: [],
      sort: [],
      daysnow: "",
    };
  },
  computed: {
    sortProduct() {
      if (this.sort.length) {
        return this.sort;
      } else {
        return this.datas;
      }
    },
  },

  methods: {
    loadTime() {
      let now = new Date();
      now.setDate(now.getDate());

      let dayNum = "";
      if (now.getDate() < 10) {
        dayNum = "0";
      }
      dayNum += now.getDate();

      let monthNum = "";
      if (now.getMonth() + 1 < 10) {
        monthNum = "0";
      }
      monthNum += now.getMonth() + 1;
      this.daysnow = dayNum + "." + monthNum + "." + now.getFullYear();
    },
    
    showData(data) {
      console.log(data);
    },
  },
  created() {
      let now = new Date();
      now.setDate(now.getDate());

      let dayNum = "";
      if (now.getDate() < 10) {
        dayNum = "0";
      }
      dayNum += now.getDate();

      let monthNum = "";
      if (now.getMonth() + 1 < 10) {
        monthNum = "0";
      }
      monthNum += now.getMonth() + 1;
      this.daysnow = dayNum + "." + monthNum + "." + now.getFullYear();
  }
};
</script>
<style >
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
.wrapper {
  padding: 40px;
  background: linear-gradient(
    90deg,
    rgba(159, 161, 155, 1) 0%,
    rgba(136, 136, 132, 1) 28%,
    rgba(148, 155, 157, 1) 42%,
    rgba(89, 87, 87, 1) 82%,
    rgba(150, 150, 150, 1) 99%
  );
  height: 100%;
}

.container {
  border-radius: 10px;
  display: flex;
  background-color: #fff;
}

.left-colum {
  width: 10%;
  border-right: 1px solid gray;
}
.right-colum {
  width: 90%;
}

.container-logo {
  display: flex;
  justify-content: center;
  align-items: center;
  margin: 20px;
}
.logo {
  padding: 20px 22px;
  margin-right: 10px;
  margin-left: 20px;
  display: flex;
  justify-content: center;
  background-color: gray;
  border-radius: 20px;
}

.button-left {
  display: flex;
  justify-content: center;
}

.button-left_request {
  border: 0;
  padding: 20px;
  background-color: rgb(87 123 249);
  color: #fff;
  font-weight: bold;
  border-radius: 15px;
  box-shadow: 1px 1px 1px 1px black;
}

.data {
  width: 100px;
  height: 100px;
  background: #fff;
}

.menu {
  margin-top: 50px;
}
.menu li {
  margin-bottom: 20px;
  font-size: 25px;
  list-style-type: none;
  padding-left: 30px;
  cursor: pointer;
}
.menu li:hover {
  background-color: rgb(199, 199, 199);
  border-left: 2px solid rgb(87 123 249);
}

.support {
  margin-top: 160px;
  display: flex;
  justify-content: center;
  font-size: 20px;
}

.button-off {
  margin: 100px auto 30px auto;
  display: flex;
  justify-content: center;
}

.nav-bar {
  border-bottom: 1px solid gray;
  display: flex;
  align-items: center;
  justify-content: space-evenly;
  padding: 20px 0;
}

.nav-bar__input {
  max-width: 300px;
  width: 100%;
}

.nav-bar__input input {
  width: 100%;
}

.nav-bar__info {
  display: flex;
  align-items: center;
  justify-content: space-between;
  width: 50%;
}

.user-name {
  display: flex;
  align-items: center;
}

.user-ava_main {
  border-radius: 50%;
  width: 50px;
  height: 50px;
  margin-left: 5px;
}

.main {
  display: flex;
}

.main-stat_select {
  margin-bottom: 40px;
}

.main-stat {
  width: 20%;
  padding-top: 20px;
  padding-right: 20px;
}
.container-stats {
  margin-top: 70px;
}
.stats-option_img {
  text-align: right;
  padding-right: 20px;
}

.stats-time {
  position: relative;
  background: rgb(173, 167, 167);
  border-radius: 50%;
  width: 120px;
  height: 120px;
  display: flex;
  align-items: center;
  margin: 20px auto;
  justify-content: center;
}
.stats-time_content {
  font-size: 16px;
  border-radius: 50%;
  width: 110px;
  height: 110px;
  display: flex;
  flex-direction: column;
  align-items: center;
  margin: 20px auto;
  justify-content: center;
  background: rgb(245, 245, 245);
}
</style>
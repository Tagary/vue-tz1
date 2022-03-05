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
            <navigation/>
        <div class="main">
          <list-people />
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
              <h2 class="stats-info_article">Projects</h2>
              <div class="stats-info">
                <div class="stats-info_container">
                  <div class="stats-info_about stats-info_total">
                    TOTAL
                    <span class="stats-info_numbers">148</span>
                  </div>
                  <div class="stats-info_about stats-info_complited">
                    COMPLITED
                    <span class="stats-info_numbers">56</span>
                  </div>
                </div>
                <div class="stats-info_container">
                  <div class="stats-info_about stats-info_inprogress">
                    IN PROGRESS
                    <span class="stats-info_numbers">76</span>
                  </div>
                  <div class="stats-info_about stats-info_waiting">
                    WAITING
                    <span class="stats-info_numbers"> 16 </span>
                  </div>
                </div>
              </div>
              <div class="declar">
                  <div class="declar-container">
                      <div class="declar-img"><img src="../public/images/message.svg" alt=""></div>
                      <div>
                          <div class="declat-txt">
                              Declaration center

                          </div>
                                                        <div class="declar-mess">
                                  Internal messages
                              </div>
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
import Navigation from './components/Navigation.vue';

export default {
  components: {
    ListPeople,
    Navigation,
  },

  data() {
    return {
      datas: [],
      sort: [],
      daysnow: "",
    };
  },


  methods: {

    
    showData(data) {
      console.log(data);
    },
  },
 
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
    font-weight: bold;;
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

.stats-info {
      border-bottom: 2px solid gray;
      padding-bottom: 100px;
}


.stats-info_article {
    margin-bottom: 20px;
}

.stats-info_container  {
    margin-bottom: 20px;
    display: flex;
    justify-content: space-between;
    text-align: center;

}
.stats-info_container div {
     display: flex;
    flex-direction: column;
    width: 100px;
    text-align: center;
    background: rgb(192, 190, 190);
    border-radius: 10px;
    padding: 10px;
}

.stats-info_numbers {
    margin-top: 10px;
    font-size: 30px;
    text-align: center;
}
.stats-info_about {
    font-size: 12px;
    text-align: start;
}

.stats-info_total span {
 border-left: 2px solid blue;
}
.stats-info_complited span {
 border-left: 2px solid green;
}
.stats-info_inprogress span {
 border-left: 2px solid aqua;
}
.stats-info_waiting span {
 border-left: 2px solid yellow;
}

.declar {
    margin-top: 20px;
    background: rgb(138, 137, 137);
    border-radius: 20px;
    height: 60px;
        display: flex;
    align-items: center;
}

.declar-container {
    display: flex;
    align-items: center;
    padding: 20px;
}
.declar-img {
    margin-right:20px;
}

.declat-txt {
    color: darkgray;
}
.declat-txt span {
 color: #000;
 font-weight: bold;
}

.declar-mess {
    font-weight: bold;
}
</style>
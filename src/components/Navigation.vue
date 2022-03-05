<template >
        <nav class="nav-bar">
          <div class="nav-bar__input">
            <input type="text" />
          </div>
          <div class="nav-bar__info">
            <div class="data" >{{ daysnow }}</div>
            <div class="alert">
              <img src="../../public/images/alert.svg" alt="" />
            </div>
            <div class="user-name">
              Cristo Parino
              <img
                class="user-ava_main"
                src="../../public/images/images.jpg"
                alt=""
              />
              <img src="../../public/images/arrowdown.svg" alt="" />
            </div>
          </div>
        </nav>
</template>
<script>
export default {
    data() {
    return {
        daysnow: "",
    }
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
}


 
</script>
<style scroped>
    
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
  justify-content: space-evenly;
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

</style>
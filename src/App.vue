<template >
    <div class="wrapper">

                    <div class="container">
            <section class="left-colum">
                <div class="container-logo">
                    <div class="logo">
                        <img src="../public/images/imglogo.svg" alt="">
                    </div>
                    <div>
                        <img src="../public/images/arrowdown.svg" alt="">
                    </div>
                </div>
                <div class="button-left">
                    <button class="button-left_request"> Request for</button>
                </div>
                    <ul class="menu">
                        <li> <img src="../public/images/dashboard.svg" alt=""> Dashbord</li>
                        <li> <img src="../public/images/people.svg" alt=""> People</li>
                        <li> <img src="../public/images/handmoney.svg" alt=""> Finances</li>
                        <li> <img src="../public/images/statistics.svg" alt=""> Statistics</li>
                        <li> <img src="../public/images/documents.svg" alt=""> Documents</li>
                        <li> <img src="../public/images/calendar.svg" alt="">Calendar</li>
                    </ul>
            <div class="support">
                <img src="../public/images/support.svg" alt="">
                Support
            </div>
            <div class="button-off">
                <img src="../public/images/buttonon.svg" alt="">
            </div>
            </section>
            <section class="right-colum">
                <nav class="nav-bar">
                    <div class="nav-bar__input">
                        <input type="text">
                    </div>
                    <div class="nav-bar__info">
                        <div class="data">{{daysnow}}</div>
                        <div class="alert">
                            <img src="../public/images/alert.svg" alt="">
                        </div>
                        <div class="user-name">
                            Cristo Parino
                            <img class="user-ava" src="../public/images/images.jpg" alt="">
                            <img src="../public/images/arrowdown.svg" alt="">
                        </div>
                    </div>
                </nav>
                <div class="main">
                    <div class="main-info">
                        <div class="main-info__title">People</div>
                        <div class="main-info__sort"><button ref="sortmenu" @click="popupVisible = !popupVisible" class="sort-by">
                            Sort By:
                            </button> 
                            <transition name="popupmenu">
                            <div class="popup" ref="popuphave" @mouseleave="changePopup" v-if="popupVisible">
                                <div @click="allSort">All</div>
                                <div @click="sortMale">Male</div>
                                <div @click="sortFemale">Female</div>
                            </div>
                            </transition>
                            </div>
                        <div class="container-card">
                            <div class="cards" v-for="data  in sortProduct" >
                            <div class="cards-user">
                                <div class="card-user_options">⋮</div>
                                <div class="cart-user_center"><img class="user-ava" :src="data.image"></div>
                                <div class="cart-user_center ">{{data.firstname}} {{data.lastname}}</div>
                                <div class="cart-user_center cart-user_email">{{data.email}}</div>
                            </div>
                        </div>
                        </div>
                    </div>
                    <div class="main-stat"></div>
                </div>
            </section>
        </div>
        </div>
</template>
<script>
import axios from 'axios';


export default {
    
    data() {
        return {
            popupVisible: false,
            checkOutSide: false, 
            datas: [],
            sort:[],
        }
    },
    computed: {
        sortProduct()  {
            if (this.sort.length) {
                return this.sort
            } else {
                return this.datas
            }
        }

        },
    

    created() {
        axios.get('https://fakerapi.it/api/v1/persons?_quantity=10').then(resp=> {this.datas = resp.data.data});
    },
    methods: {
        
        sortMale: function() {
            let thisNf = this;
            thisNf.sort = []; 
           this.datas.map(item => {
                if(item.gender == 'male') {
                   thisNf.sort.push(item);
                }
            })
        },
        sortFemale: function() {
            let thisNf = this;
            thisNf.sort = []; 
           this.datas.map(item => {
                if(item.gender == 'female') {
                   thisNf.sort.push(item);
                }
            })
        },
        allSort: function() {
            let thisNf = this;
            thisNf.sort = [];
            thisNf.sort = thisNf.datas; 
        },
        changePopup: function()  {
            let thisNf = this;
            document.addEventListener('click', function(item) {
                if(item.target !== thisNf.$refs.popuphave ) {
                    thisNf.popupVisible = false;
                
                }
                if(item.target === thisNf.$refs.sortmenu) {
                    thisNf.popupVisible = true;
                }
            })
            }

    },
}
</script>
<style >
    * {
        margin: 0;
        padding: 0;
        box-sizing: border-box;
        }
         .wrapper {
                padding: 40px;
        background: linear-gradient(90deg, rgba(159,161,155,1) 0%, rgba(136,136,132,1) 28%, rgba(148,155,157,1) 42%, rgba(89,87,87,1) 82%, rgba(150,150,150,1) 99%);
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
    margin: 20px ;

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

    .nav-bar__info{ display: flex; align-items: center; justify-content: space-between; width: 50%;}

    .user-name {
        display: flex;
        align-items: center;
        
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

    .user-ava {
        border-radius: 50%;
        width: 50px;
        height: 50px;
    }

    .cart-user_center {
        text-align: center;
    }

    .main {
        display: flex;
        
    }

    .main-info {
        width: 80%;
        padding: 20px;
    }
    .main-stat {
        width: 20%;
    }

    .popup {
        position: absolute;
        top: 0;
        left: 60px;
        background-color: rgb(214, 207, 207);
        padding: 10px;
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

    .popupmenu-enter-active, .popupmenu-leave-active {
        transition: ease-in-out 0.5s;
    }
    .popupmenu-enter, .popupmenu-leave-to {
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
</style>
<script setup>
import { ref } from 'vue';
import TheHeaderComponent from './TheHeaderComponent.vue';
import TheSearchbarComponent from './TheSearchbarComponent.vue';
import axios  from 'axios'

const userData = ref(null)
const username = ref('')
const errMessage = ref('')

async function searchUser() {
    try {
    const data = await axios.get(`https://api.github.com/users/${username.value}`).then(({ data }) => {
            console.log(data)

            userData.value = data;
        })
        console.log(data);
    } catch (error) {
        console.error(error);
        errMessage.value = 'No results';
        userData.value = null;
    }
    username.value = ""
}


</script>

<template>

<TheHeaderComponent/>
    
<div class="content">
    
    
<TheSearchbarComponent>
        
        <div class="input-icons">
            <i class="fa fa-search icon"></i>
            <input class="input-field" type="text" v-model="username" placeholder="Search GitHub username…">
        </div>
            
        <button @click.prevent="searchUser" class="btn">Search</button>

</TheSearchbarComponent> 


    <div class="profile">    
            
    <div class="pic">
            
        <img class="profilepic" :src="userData?.avatar_url" alt="">
    
    </div>
            
    <div class="bioname">
                
        <div>
                    
            <h1 class="namedetails">{{ userData?.name }}</h1>
                    
            <p class="handle">{{ userData?.login }}</p>
        
        </div>
        
        <div class="div">
                    
            <p class="joined">{{ userData?.created_at }}</p>
                
        </div>
            
    </div>
            
    <div class="profiledetails">
                
        <p v-if="userData?.bio">{{ userData?.bio   }}</p>
                
        <p v-else>This profile has no bio</p>
            
    </div>
            
    <div class="counters">
                
        <div class="repos">
                    
            <p class="title">Repos</p>
                    
            <p class="count">{{ userData?.public_repos }}</p>
                
        </div>
                
        <div class="repos">
                    
            <p class="title">Followers</p>
                    
            <p class="count">{{ userData?.followers }}</p>
                
        </div>
                
        <div class="repos">
                    
            <p class="title">Following</p>
                    
            <p class="count">{{ userData?.following }}</p>
                
        </div>
            
    </div>
            
    <div class="social">
                
        <p  v-if="userData?.location"><i class="fa fa-map-marker fa-2x"></i> {{ userData?.location }}</p>
                
        <p v-else> Not Available</p>
                
        <p v-if="userData?.blog">
            
            <img src="../assets/002-url.svg" alt="">
            {{ userData?.blog }}
                
        </p>
        <p v-if="userData?.twitter_username"><i class="fa fa-twitter fa-2x"></i> {{ userData?.twitter_username }}</p>
            
        <p v-else> Not Available</p>
                
        <p v-if="userData?.company">
            
            <img src="../assets/001-office-building.svg" alt=""> {{ userData?.company }}
        
        </p>
            <p v-else> Not Available</p>
        
        </div>
            
        </div>
    </div>
</template>

<style scoped>
.btn {
    padding: 13px 16px;
    border-radius: 10px;
    background: #0079FF;
    border: none;
    color: #fff;
}
    
.input-icons i {
    position: absolute;
}

.input-icons {
    width: 100%;
    margin-bottom: 10px;
}

.icon {
    padding: 12px;
    color: #0079FF;
    min-width: 50px;
    height: 20px;
    text-align: center;
    margin-top: 11px;
}

.input-field {
    width: 100%;
    margin-top: 10px;
    padding: 10px 5px 10px 40px;
    text-align: center;
    background-color: transparent;
    border: none;
    color: #2B3442;
    font-size: 13px;
    font-weight: 400;
    line-height: 25px;
    text-align: start;
    }

.content{
    margin: 35px 0 14px 0;
    display: flex;
    flex-direction: column;
    gap: 20px;
    border-radius: 15px;
    

}
.profile{
     display: grid !important;
     border-radius: 15px;
     background: #FEFEFE;
     gap: 20px 20px;
     padding: 7% 5%;
     box-shadow: 0px 16px 30px -10px rgba(70, 96, 187, 0.20);
}
.pic {
    grid-column: 1 / 2;
    text-align: center; 
}

.profilepic {
    width: 70px;
    height: 70px;
    border-radius: 50%; 
    border: none; 
}

.bioname{
    grid-column: 2 / 12;
}
.namedetails{
    color: #2B3442;
    font-size: 16px;
    font-weight: 700;
    line-height: normal;
    text-align: left;
}
.handle{
    color: #0079FF;
    font-size: 13px;
    font-weight: 400;
}

.joined{
    color: #2B3442;
    font-size: 13px;
    font-weight: 400;
}
.profiledetails {
        grid-column: 1 / 12;
        color: #2B3442;
        font-size: 13px;
        font-weight: 400;
        line-height: 25px; 
    }

.counters{
        grid-column: 1 / 12;
        padding: 15px 32px;
        display: flex;
        justify-content: space-between;
        border-radius: 10px;
        background: #F6F8FF;
    }
.repos{
        display: flex;
        flex-direction: column;
        gap: 10px;
    }
.repos .title{
     color: #2B3442;
        text-align: center;
        font-size: 11px;
        font-weight: 400;
    }
.repos .count{
    color: #2B3442;
    font-size: 16px;
    font-weight: 700;
    }
.social{
        grid-column: 1 / 12;
        display: grid;
        grid-template-columns: 1fr;
        gap: 10px;
        color: #2B3442;
    }
.social p{
       color: #2B3442;
        font-size: 13px;
        font-weight: 400;
        display: flex;
        align-items: center;
        gap: 15px;

}
    

@media (min-width: 490px){
.social{
    grid-template-columns: repeat(2, 1fr);

}
.profilepic{
    width: 117px;
    height: 117px;
}

.namedetails{
    font-size: 26px;
}

.handle{
    font-size: 16px;
}

.joined{
    font-size: 15px;
}
.profiledetails{
            font-size: 15px;
        }
        .repos .title{
            font-size: 13px;
        }
        .repos .count{
            font-size: 22px;
        }
}

@media (min-width: 768px){
.social{
        grid-template-columns: repeat(2, 1fr);
}

.profilepic{
        width: 117px;
        height: 117px;
        }
.namedetails{
        font-size: 26px;
        }
.handle{
        font-size: 16px;
        }

.joined{
        font-size: 15px;
        }
.profiledetails{
        grid-column: 2 / 12;
        font-size: 15px;
}

.counters{
        grid-column: 2 / 12;
}

.bioname{
        display: flex;
        justify-content: space-between;
}
.profiledetails{
        font-size: 15px;
}
.repos .title{
        font-size: 13px;
}

.repos .count{
        font-size: 22px;
}
.social{
        grid-column: 2 / 12;
        grid-template-columns: repeat(2, 1fr);
    }
}

</style>
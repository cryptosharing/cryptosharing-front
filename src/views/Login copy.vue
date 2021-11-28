<!--
 * 严肃声明：
 * 开源版本请务必保留此注释头信息，若删除我方将保留所有法律责任追究！
 * 本系统已申请软件著作权，受国家版权局知识产权以及国家计算机软件著作权保护！
 * 可正常分享和学习源码，不得用于违法犯罪活动，违者必究！
 * Copyright (c) 2020 sherard all rights reserved.
 * 版权所有，侵权必究！
 *
-->

<template>
  <div class="container">
    <div class="home">
      <div class="header">
        <div class="title"><img src="../assets/logo_white.svg">BliTok</div>
        <!-- <div class="contact">Contact</div> -->
        <div class="contact">
          <TwitterOutlined style="margin-right:14px;"  @click="drillDown('twitter')"/>
          <GithubOutlined style="margin-right:14px;" @click="drillDown('git')"/>
          <img style="height:24px;margin-right:14px;"  @click="drillDown('telegram')" src="../assets/telegram.svg">
          <img style="height:24px;margin-right:14px;" @click="drillDown('book')" src="../assets/book.svg">
        </div>
      </div>
      <div class="content">
        <div class="main-content">
          <p>The first short-video Dapp with NFT-enabled incentive</p> 
          <p> on the blockchain!</p> 
        </div>
        <div class="sub-content">
          Both video-creators and video-viewers can create value here.
        </div>
        <div class="btn">
          <a-button class="login" type="primary" @click="goTo">Get Started Now</a-button>
        </div>
      </div>
      <div class="overview">
        <img src="./../assets/shot.jpg"/>
      </div>
    </div>

    <div class="intro">
      <div class="header">
        <div class="title">How Blitok Fascinates The World?</div>
      </div>
      <div class="content">
        <div class="text">
          <p class="title"> NFT-Enabled Incentive</p>
          <p class="word"> Get considerable incentive in our autonomous NFT-driven short-video platform no matter you are a video-maker or a fan.</p>
        </div> 
        <img src="../assets/chatou.svg">
      </div>
      <div class="content2">
        <img src="../assets/gragon.svg">
        <div class="text">
          <p class="title"> Modern Investment</p>
          <p class="word"> Share the success with the celebrities and enjoy the growing value of NFT. Stake TOK in the liquidity pool.</p>
        </div> 
      </div>
      <div class="content">
        <div class="text">
          <p class="title"> NFT Gallery</p>
          <p class="word"> Show your own NFTs in your videos, sell them for profits or buy what you are fond of.</p>
        </div> 
        <img src="../assets/fish.svg">
      </div>
      <div class="content2">
        <img src="../assets/goast.svg">
        <div class="text">
          <p class="title"> Elastic Experience</p>
          <p class="word">Lightweight smart contracts, migratable framework, and friendly user experience.</p>
        </div> 
      </div>

    </div>


    <div class="team">
      <p class="title">
        THE TEAM IS COMPSED OF YOUNG, PASSIONATE, AND CREATIVE SOULS WITH  
      </p>
      <p class="title">
         BLOCKCHAIN EXPERTISE AND PRACTICAL EXPERIENCE. 
      </p>
      <div class="ceo">
        <div class="member">
          <img src="../assets/toast_2.png">
          <div class="name">Barron Cheng</div>
          <div class="desc">
            <p>He is a Ph.D from ZJU. He has been focused on blockchain research for more than four years and has published some blockchain-related academic papers in several international conferences and transactions. He also participated in many top blockchain projects and made outstanding contributions.</p>
          </div>
        </div>

        <div class="member">
          <img src="../assets/toast_1.png">
          <div class="name">Kimos Li</div>
          <div class="desc">
            <p>He has many years of practical experence on blockchain, proficient in various blockchain ecology and corresponding development framework. He has led many blockchain projects. Now he is pursuing a Ph.D in the School of Computer Science and Technology of ZJU.</p>
          </div>
        </div>

        <div class="member">
          <img src="../assets/toast_3.png">
          <div class="name">Jason Zhou</div>
          <div class="desc">
            <p>He has a master's degree in computer science from ZJU and a senior member of the blockchain Club of ZJU. He has rich experience in Internet product development and blockchain technology development, and is familiar with various open source tools and blockchain frameworks.   </p>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import { useRouter } from 'vue-router'
import { notification } from 'ant-design-vue';
import { resetUser,setUser} from '../store/user'
import { TwitterOutlined ,GithubOutlined} from '@ant-design/icons-vue';
export default {
    components: {
    TwitterOutlined,
    GithubOutlined
  },
  setup() {
    resetUser();
    const router = useRouter()
    // get started
    const goTo = async () => {
      if (typeof window.ethereum != 'undefined') {
        const accounts = await window.ethereum.request({ method: 'eth_requestAccounts' });
        const accountId = accounts[0];
        setUser({accountId,authTime:new Date().getTime(),isLogin:true})
        router.push({ path: '/home'})
      }else{
        notification.warning({
          message: 'You should install MetaMask first! ',
        });
      }
    }

    const drillDown = (str)=>{
      if(str =='git') {
        window.open('https://github.com/BliTok');
      }else if(str =='book') {
        window.open('https://blitok.oss-cn-beijing.aliyuncs.com/blitok%E7%99%BD%E7%9A%AE%E4%B9%A6.pdf');
      }else if(str =='twitter') {
        window.open('https://twitter.com/HightSigb');
      }else if(str =='telegram') {
        window.open('https://t.me/joinchat/DGvJsqsU9jkzYmQ1');
      }
    }
    return {
      goTo,
      drillDown
    }
  }
}
</script>

<style lang="less">
  .container {
    .home {
      height: 100vh;
      background-image: linear-gradient(#3ebac0, #42c8a6);
      padding: 2% 5%;
      box-sizing: border-box;
      color: white;
      display: flex;
      flex-direction: column;

      .header {
        display: flex;
        align-items: baseline;
        justify-content: space-between;
        flex: 0 0 10%;

        .title {
          font-size: 24px;
          font-weight: 600;
          display: flex;
          align-items: center;

          img {
            height: 20px;
            margin-right: 2px;
          }
        }

        .contact {
          display: flex;
          font-size: 24px;

          > span,
          img {
            cursor: pointer;
          }
        }
      }

      .content {
        flex: 0 0 35%;
        display: flex;
        flex-direction: column;
        justify-content: space-around;
        
        .main-content {
          letter-spacing: 0px;
          color: #ffffff;
          white-space: normal;
          font-size: 34px;
          font-weight: 600;
          text-align: center;
        }

        .sub-content {
          text-align: center;
          color: #d6f7f2;
          font-family: 'Open Sans', sans-serif;
          font-size: 16px;
          line-height: 1.6;
          font-weight: 400;
        }

        .btn {
          text-align: center;

          button {
            width: 140px;
            font-size: 14px;
            padding: 0;
            height: 44px;
            margin-top: 30px;
            background: #2e3038;
            border-color: #2e3038;
          }
        }
      }

      .overview {
        text-align: center;
        flex: 0 0 55%;

        img {
          height: 20vw;
          width: auto;
          margin-top: 20px;
        }
      }
    }

    .intro {
      height: 100vh;
      padding: 2% 5%;
      box-sizing: border-box;
      background: #ffffff;
      background-image: linear-gradient(#3ebac0, #42c8a6);

      .header {
        height: 10%;
        text-align: center;
        letter-spacing: 0px;
        color: #ffffff;
        white-space: normal;
        margin-bottom: 5%;
        font-size: 38px;
        margin-top: 1%;
        font-weight: 600;
      }

      .content {
        display: flex;
        margin-left: calc(50% - 410px);
        margin-bottom: -2%;

        .text {
          flex: 0 0 280px;
          margin-left: 3%;

          .title {
            text-align: left;
            letter-spacing: 0px;
            color: #ffffff;
            opacity: 1;
            font-size: 24px;
            font-weight: 500;
            line-height: 24px;
            margin-bottom: 10px;
          }

          .word {
            text-align: left;
            font-size: 16px;
            letter-spacing: 0px;
            color: #ffffff;
            opacity: 1;
          }
        }

        img {
            margin-right: 10px;
            height: 90px;
            width: 90px;
          }
      }

      .content2 {
        display: flex;
        justify-content: flex-end;
        margin-right: calc(50% - 410px);
        margin-bottom: -2%;

        img {
            margin-right: 10px;
            height: 90px;
            width: 90px;
          }

        .text {
          flex: 0 0 291px;
          margin-right: 3%;

          .title {
            text-align: left;
            letter-spacing: 0px;
            color: #ffffff;
            opacity: 1;
            font-size: 24px;
            font-weight: 500;
            line-height: 24px;
            margin-bottom: 10px;
          }

          .word {
            text-align: left;
            font-size: 16px;
            letter-spacing: 0px;
            color: #ffffff;
            opacity: 1;
          }
        }
      }
    }

    .team {
      height: 100vh;
      padding: 2% 5%;
      box-sizing: border-box;
      background: #ffffff;

      .title {
        text-align: center;
        font-size: 24px;
        color: #333;
        text-transform: uppercase;
        font-family: 'Raleway', sans-serif;
        font-weight: 700;
        margin: 30px 0px;
        line-height: 1;
        letter-spacing: 1.5px;
      }

      .sub-title {
        color:#989898;
        text-align: center;
        font-size: 14px;
      }

      .ceo {
        display: flex;

        .member {
          width: 315px;
          border: 1px solid #e1e1e1;
          text-align: center;
          margin: 0 auto;
          background: #ffffff;
          height: 570px;

          img {
            width: 315px;
          }

          .name {
            font-size: 16px;
            color: #333;
            text-transform: uppercase;
            font-family: 'Raleway', sans-serif;
            font-weight: 700;
            margin-top: 0px;
            line-height: 1.3;
            letter-spacing: 1.5px;
            margin: 16px 30px;
          }

          .desc {
            font-family: 'Open Sans', sans-serif;
            font-size: 14px;
            color: #666666;
            line-height: 1.6;
            font-weight: 400;
            margin: 0 25px;
            margin-bottom: 15px;
          }
        }
      }

      
    }
  }
</style>

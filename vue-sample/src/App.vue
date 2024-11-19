<script setup>
import { ref, onMounted } from "vue";

const menuItems = [
  "白頭翁的特性",
  "白頭翁的故事",
  "白頭翁的美照",
  "白頭翁的危機",
];

const sections = [
  {
    title: "外觀",
    content:
      "白頭鵯體長約17到22公分，額至頭頂純黑色而富有光澤，兩眼上方至後枕白色，形成一白色枕環。耳羽後部有一白斑，此白環與白斑在黑色的頭部均極為醒目，老鳥的枕羽(後頭部)更潔白，所以又叫「白頭翁」。",
  },
  {
    title: "棲地",
    content:
      " 白頭翁和麻雀、綠繡眼合稱「城市三寶」，常成群出現在平原區灌木叢、丘陵樹林地帶，以及校園、公園、庭院、行道中的各種高高的電線與樹上。",
  },
  {
    title: "食性",
    content:
      " 以果樹的漿果和種子為主食，並時常飛入果園偷吃果實，還會吃嫩葉嫩芽，尤其是胡蝶蘭的嫩葉嫩芽葉，偶爾啄食昆蟲。",
  },
];
const activeIndex = ref(null);

const setActive = (index) => {
  activeIndex.value = index;
};
const isHeaderActive = ref(true);
const toggleHeader = () => {
  isHeaderActive.value = !isHeaderActive.value;
  console.log(isHeaderActive.value);
};
</script>

<template>
  <div class="common-layout">
    <el-container>
      <el-aside class="aside" v-show="false">
        <div class="aside-icon">
          <div class="head"></div>
          <div class="beak"></div>
          <div class="face"></div>
          <div class="eye"></div>
        </div>
        <div class="aside-title">白頭翁不吃小米</div>
        <div class="item-block">
          <div
            class="aside-item"
            v-for="(item, index) in menuItems"
            :key="index"
            :class="{ active: activeIndex === index }"
            @click="setActive(index)"
          >
            {{ item }}
          </div>
        </div>
      </el-aside>
      <el-container>
        <el-header
          class="header"
          :class="{ headerActive: isHeaderActive }"
          v-show="true"
        >
          <div class="header-menu" @click="toggleHeader">X</div>
          <div class="header-title">白頭翁不吃小米</div>
          <div class="header-icon">
            <div class="head"></div>
            <div class="beak"></div>
            <div class="face"></div>
            <div class="eye"></div>
          </div>
          <div class="content-block" v-show="isHeaderActive">
            <div
              class="head-content"
              v-for="(item, index) in menuItems"
              :key="index"
              :class="{ active: activeIndex === index }"
              @click="setActive(index)"
            >
              {{ item }}
            </div>
          </div>
        </el-header>

        <el-main class="main">
          <div class="main-title">白頭翁 (Chinese bulbul)</div>
          <div class="main-content">
            又名白頭鵯。以果實、昆蟲為主食，無法消化小米、穀類。平均壽命約 8~10
            年。
          </div>
          <div class="img-mask">
            <img
              src="https://s3-alpha-sig.figma.com/img/0411/a36a/2789ca730221661c9008e0bf404c1cdc?Expires=1733097600&Key-Pair-Id=APKAQ4GOSFWCVNEHN3O4&Signature=Sk6jJrNXZ54chnO3TTyZz6RjuvTOeBSAa2E0uv0774ck~4W0o3l2JdQcGpzu-h24cpZnSWUAk8WfRZRRAUh8RR-8nFTpH8-9QSawyQZ2XInMeZ9panE4la~bXflXJ4cfrFoWIMenKdQQDCXBnXGJ-jKgedlNFjS5gxu~eIoiZQAEGI5tU9cRfamgfwgZyDtR363HTvLhFMSOBdrbDmTl4yFvJ3KSAbramlxH820EJyCJR0W2CNrpcopFPe243OEeL~vNmkw~SgGkqV-7JETEXmSy1vFroaBlo26L6EtpMWJqKNyuYu7mFu7qgavmsQ9aAMDrfQy2k5VXeHonnjAiyA__"
              alt=""
            />
          </div>
        </el-main>

        <el-footer class="footer">
          <div class="footer-div" v-for="item in sections">
            <div class="title-icon" />
            <div class="footer-title">{{ item.title }}</div>
            <div class="footer-content">
              {{ item.content }}
            </div>
          </div>
        </el-footer>
      </el-container>
    </el-container>
  </div>
</template>

<style scoped>
* {
  font-family: "Noto Sans", sans-serif;
}
.aside {
  background-color: white;
  width: 345px;
  height: 1002px;
  position: relative;
  overflow: visible;

  .aside-icon {
    position: absolute;
    top: 47.31px;
    left: 296.22px;
    width: 97.56px;
    height: 97.56px;
    background-color: white;
    border-radius: 50%;
    box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
    overflow: hidden;
    text-align: center;
    display: flex;
    justify-content: center;
    align-items: center;
    z-index: 9999;

    .head,
    .face,
    .beak,
    .eye {
      position: absolute;
      background-color: black;
    }

    .head {
      border-radius: 51% 33% 36% 20% / 49% 32% 45% 0%;
      width: 60%;
      height: 50%;
      z-index: 1;
    }

    .face {
      border-radius: 40% 32% 28% 20% / 65% 42% 34% 0%;
      background-color: white;
      width: 60%;
      height: 30%;
      z-index: 3;
    }

    .eye {
      width: 10px;
      height: 10px;
      border-radius: 50%;
      top: 45%;
      left: 60%;
      transform: translateX(-50%);
      z-index: 4;
    }

    .beak {
      width: 30px;
      height: 10px;
      border-radius: 40% 60% 28% 20% / 0% 100% 0% 0%;
      top: 40%;
      left: 80%;
      transform: translateX(-50%) rotate(-10deg);
      z-index: 2;
    }
  }

  .aside-title {
    margin: 78.33px 67.5px;
    width: 210px;
    height: 41px;
    font-size: 30px;
    font-weight: 700;
    line-height: 40.86px;
    text-align: left;
  }

  .item-block {
    margin-top: 75.67px;
    margin-inline: 118.5px;
    padding-bottom: 0px;
  }

  .aside-item {
    font-size: 18px;
    font-weight: 700;
    line-height: 40.86px;
    text-align: center;
  }

  .aside-item:hover,
  .aside-item.active {
    color: #aa6666;
    text-decoration-line: underline;
    text-decoration-color: #aa6666;
    text-decoration-thickness: 2px;
    text-underline-offset: 4.21px;
  }
}

.main {
  width: 1095px;
  height: 634.21px;
  position: relative;
  overflow: hidden;

  .main-title {
    font-size: 48px;
    font-weight: 700;
    line-height: 65.38px;
    color: white;
    position: absolute;
    top: 503.36px;
    right: 44.75px;
    bottom: 65.85px;
    left: 506.25px;
  }

  .main-content {
    font-size: 18px;
    font-weight: 400;
    line-height: 24.52px;
    color: white;
    position: absolute;
    top: 572.36px;
    right: 44.75px;
    bottom: 36.85px;
    left: 405.25px;
  }

  .img-mask {
    width: auto;
    height: 634.21px;
  }

  .img-mask img {
    position: absolute;
    width: 2034px;
    height: 1110.88px;
    top: -234.06px;
    right: -312.4px;
    bottom: -246.61px;
    left: -626.6px;
    z-index: -1;
  }
}

.footer {
  background-color: #dcccbc;
  width: 1095px;
  height: 367.15px;
  display: flex;
  overflow: hidden;

  .footer-div {
    width: 278.51px;
    height: 225px;
    margin: 58px 0px 85px 58px;
    position: relative;
  }

  .footer-div:nth-child(1) {
    margin-left: 50.74px;
  }

  .footer-div:last-child {
    margin-right: 50.74px;
  }

  .footer-title {
    width: 36px;
    height: 80px;
    font-size: 36px;
    font-weight: 700;
    line-height: 40px;
    position: absolute;
    right: 37.84px;
    bottom: 145px;
    left: 5px;
  }

  .title-icon {
    width: 25px;
    height: 25px;
    background-color: transparent;
    border: 8px solid rgba(170, 102, 102, 0.6);
    border-radius: 50%;
    box-sizing: border-box;
    background: transparent;
    position: absolute;
    top: 66.58px;
    right: 221.57px;
    bottom: 113.42px;
    left: 31.94px;
  }

  .footer-content {
    font-size: 16px;
    font-weight: 400;
    line-height: 21.79px;
    width: 199.66px;
    height: 176px;
    position: absolute;
    bottom: 49px;
    left: 78.84px;
  }
}

@media (max-width: 376px) {
  .header {
    height: 87.74px;
    width: 100%;
    min-width: 286.43px;
    position: relative;
  }

  .headerActive {
    height: 286.43px;
  }

  .header-menu {
    height: 18px;
    width: 24px;
    text-align: center;
    border: 2px solid black;
    position: absolute;
    inset: 34.87px 324.62px 34.87px 26.38px;
  }

  .header-title {
    position: absolute;
    inset: 30.37px 117.5px;
    width: 140px;
    height: 27px;
    font-size: 20px;
    font-weight: 700;
    line-height: 27.24px;
  }
  .header-icon {
    position: absolute;
    height: 48.78px;
    width: 48.52px;
    inset: 19.61px 18.84px 19.61px 307.38px;
    background-color: white;
    border-radius: 50%;
    box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
    overflow: hidden;
    text-align: center;
    display: flex;
    justify-content: center;
    align-items: center;
    z-index: 9999;

    .head,
    .face,
    .beak,
    .eye {
      position: absolute;
      background-color: black;
    }

    .head {
      border-radius: 51% 33% 36% 20% / 49% 32% 45% 0%;
      width: 60%;
      height: 50%;
      z-index: 1;
    }

    .face {
      border-radius: 40% 32% 28% 20% / 65% 42% 34% 0%;
      background-color: white;
      width: 60%;
      height: 30%;
      z-index: 3;
    }

    .eye {
      width: 6px;
      height: 6px;
      border-radius: 50%;
      top: 45%;
      left: 60%;
      transform: translateX(-50%);
      z-index: 4;
    }

    .beak {
      width: 15px;
      height: 5px;
      border-radius: 40% 60% 28% 20% / 0% 100% 0% 0%;
      top: 40%;
      left: 80%;
      transform: translateX(-50%) rotate(-10deg);
      z-index: 2;
    }
  }

  .content-block {
    position: absolute;
    width: 127px;
    height: 149.21px;
    inset: 92px 124px 45.22px 124px;
  }

  .head-content {
    width: 127px;
    height: 25px;
    font-size: 18px;
    font-weight: 400;
    line-height: 24.52px;
    text-align: center;
    margin-bottom: 21.74px;
  }

  .head-content:hover,
  .head-content.active {
    color: #aa6666;
    text-decoration-line: underline;
    text-decoration-color: #aa6666;
    text-decoration-thickness: 2px;
    text-underline-offset: 4.21px;
  }

  .main {
    width: 375px;
    height: 311.4px;
    position: relative;
    overflow: hidden;

    .main-title {
      /* font-size: 48px;
      font-weight: 700;
      line-height: 65.38px;
      color: white;
      position: absolute;
      top: 503.36px;
      right: 44.75px;
      bottom: 65.85px;
      left: 506.25px; */
    }

    .main-content {
      /* font-size: 18px;
      font-weight: 400;
      line-height: 24.52px;
      color: white;
      position: absolute;
      top: 572.36px;
      right: 44.75px;
      bottom: 36.85px;
      left: 405.25px; */
    }

    .img-mask {
      /* width: auto;
      height: 634.21px; */
    }

    .img-mask img {
      /* position: absolute;
      width: 2034px;
      height: 1110.88px;
      top: -234.06px;
      right: -312.4px;
      bottom: -246.61px;
      left: -626.6px;
      z-index: -1; */
    }
  }

  .footer {
    background-color: #dcccbc;
    width: 375px;
    height: auto;
    display: flex; /* 啟用 Flexbox */
    flex-direction: column; /* 垂直排列 */
    align-items: center; /* 選擇是否水平置中 */
    padding-top: 50.86px;

    .footer-div {
      width: 302.24px;
      height: 176px;
      margin-top: 50.5px;
      margin-inline: 36.38px;
      position: relative;
    }

    .footer-div:nth-child(1) {
      margin-top: 50.86px;
    }

    .footer-title {
      width: 36px;
      height: 80px;
      font-size: 36px;
      font-weight: 700;
      line-height: 40px;
      position: absolute;
      right: 37.84px;
      bottom: 145px;
      left: 5px;
    }

    .title-icon {
      width: 25px;
      height: 25px;
      background-color: transparent;
      border: 8px solid rgba(170, 102, 102, 0.6);
      border-radius: 50%;
      box-sizing: border-box;
      position: absolute;
      top: 13px;
      right: 244.3px;
      bottom: 19.42px;
      left: 32.94px;
    }

    .footer-content {
      font-size: 16px;
      font-weight: 400;
      line-height: 21.79px;
      width: 199.66px;
      height: 176px;
      position: absolute;
      bottom: 49px;
      left: 78.84px;
    }
  }
}
</style>

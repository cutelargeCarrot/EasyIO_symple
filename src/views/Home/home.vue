<template>
    <div class="Home flex">
        <div class="title">{{ sayTime }} {{ store.username }}</div>
        <div class="center flex">
            <div>
                <div class="pic btn flex" @click="jump('/main/center')">
                    <img src="@/assets/icon/图片.png" />
                </div>
                <div class="vid btn flex" @click="jump('/main/two')">
                    <img src="@/assets/icon/视频.png" />
                </div>
            </div>
            <div>
                <div class="fil btn flex" @click="jump('/main/three')">
                    <img src="@/assets/icon/文件.png" />
                </div>
                <div class="num btn flex" @click="jump('/main/user')">
                    <img class="img" src="@/assets/icon/统计.png" />
                </div>
            </div>
        </div>
        <!-- 备案号 -->
          <div class="bottom">
            <a href="https://beian.miit.gov.cn">津ICP备2022007072号-1</a>
        </div>
    </div>
  
</template>

<script setup>
import { ref, onMounted } from "vue";
import { useRouter } from "vue-router";
import { useCounterStore } from "@/stores/user";
import useGetTime from "@/hooks/useGetTime";
const store = useCounterStore();
let router = useRouter();
let sayTime = ref("");

function jump(val) {
    router.push(val);
}
onMounted(() => {
    sayTime.value = useGetTime();
});
</script>

<style lang="scss" scoped>
.Home {
    flex: 1;
    flex-direction: column;
    margin: 20px;
    padding: 20px;
    background-color: #fff;
    background: linear-gradient(
            rgba(255, 255, 255, 0.9),
            rgba(255, 255, 255, 0.9)
        ),
        url("@/assets/imgs/logo_blue.png") no-repeat 50% 50%/ 40% 40%;

    .title {
        margin: 10px 20px;
        font-size: 20px;
        height: 50px;
        line-height: 50px;
        color: var(--color);
        text-align: center;
        border-bottom: 1px solid var(--color);
    }
    .center {
        flex: 1;
        height: calc(100% - 150px);
        padding: 50px 20px;
        justify-content: center;
        align-items: center;
        div {
            display: flex;
            height: 100%;
            width: 100%;
            flex-direction: row;
            justify-content: space-evenly;
            .btn {
                justify-content: center;
                align-items: center;
                transition: 0.8s;
                // border: 1px solid var(--gray);
                border: 0;
                padding: 40px;
                background-color: rgba(255, 255, 255, 0.1);
                img {
                    width: 30%;
                    transition: 0.8s;
                }
                .img {
                    width: 40%;
                }
            }
            .btn:hover {
                opacity: 0.6;
                border-left: 2px solid var(--color);
                border-right: 2px solid var(--color);
                border: 2px solid rgba(151, 189, 255, 0.5);
                box-shadow: 0 0 8px 4px var(--gray);
                font-size: 30px;

                background: linear-gradient(
                    rgba(151, 167, 255, 0.2),
                    rgba(135, 189, 255, 0.2)
                );
            }
            .pic:hover,
            .vid:hover,
            .fil:hover,
            .num:hover {
                img {
                    // display: none;
                    width: 0;
                    // height: 0;
                }
            }
            .pic:hover::before {
                content: "图";
            }
            .pic:hover::after {
                content: "片";
            }
            .vid:hover::before {
                content: "视";
            }
            .vid:hover::after {
                content: "频";
            }
            .fil:hover::before {
                content: "文";
            }
            .fil:hover::after {
                content: "件";
            }
            .num:hover::before {
                content: "统";
            }
            .num:hover::after {
                content: "计";
            }
        }
    }
    .bottom{
        height: 20px;
        text-align: center;
        a{
        text-decoration: underline;
        }
    }
    .bottom:hover{
        a{
            color:var(--color);
        }
    }
}

@media screen and (max-width: 950px) {

    .Home {
        .center {
            height: calc(100% - 150px);
            padding: 50px 20px;
            justify-content: center;
            align-items: center;
            div {
                display: flex;
                flex: 1;
                width: 100%;
                flex-direction: column;
                align-items: center;
                justify-content: space-evenly;
                .btn {
                    height: 80px;
                    width: 120px;
                    justify-content: center;
                    align-items: center;
                    transition: all 1s;
                    padding: 0;
                    margin: 10px 0;
                    background-color: rgba(255, 255, 255, 0.1);
                    border: 0;
                    img,
                    .img {
                        height: 80px;
                        width: 80px;
                    }
                }
                .btn:hover {
                    opacity: 0.6;
                    border-left: 2px solid var(--color);
                    border-right: 2px solid var(--color);
                    border: 2px solid rgba(151, 189, 255, 0.5);
                    box-shadow: 0 0 8px 4px var(--gray);
                    background: linear-gradient(
                        rgba(151, 167, 255, 0.2),
                        rgba(135, 189, 255, 0.2)
                    );
                }
                  .pic:hover,
            .vid:hover,
            .fil:hover,
            .num:hover {
                img {
                    // display: none;
                    // width: 0;
                    height: 0;
                }
            }
            }
        }
    }
}
@media screen and (max-width: 600px) {
    .Home{
        .center{
            flex-direction: column;
          div{
              .btn{
                border-bottom:1px solid var(--gray) ;
                overflow: hidden;
            }
          }
        }
        margin-bottom: 100px;
    }
}
</style>
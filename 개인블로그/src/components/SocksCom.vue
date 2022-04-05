<template>
    <div id="content">
        <section id="main-section">
            <article>
                <div class="nav-bar"></div>

                <!-- 1. 클릭시 장바구니 개수 표시 -->
                <div class="cart">장바구니개수( {{ count.length }} )</div>

                <div class="product-display">
                    <div class="product-container">
                        <div class="product-image">
                            <!-- 2. 이미지 변경   -->
                            <img v-bind:src="pic" v-bind:alt="socksimage" />
                        </div>

                        <div class="product-info">
                            <!-- 3. 상품명을 data 변수에 추가 -->
                            <h1>{{ productname }}</h1>
                            <!-- 4. 목록을 반복문으로 표시 -->
                            <ul>
                                <li v-for="(item, index) in list" :key="index">
                                    {{ item }}
                                </li>
                            </ul>

                            <!-- 5. 뷰 데이터로 id, color, image 객체배열을 정의하고 반복문으로 수정후 출력 -->
                            <!-- 5. id : 임의숫자4자리 -->
                            <!-- 5. color : blue, green  -->
                            <!-- 5. image : 이미지 경로 설정 -->
                            <div
                                v-for="(list, index) in products"
                                :key="index"
                                class="color-circle"
                                :style="{ 'background-color': list.color }"
                                v-on:mouseover="change(index)"
                            ></div>
                            <!-- 6. 장바구니 버튼 클릭 시 상단 장바구니개수( ) 출력위치에 표시 -->
                            <button class="button" v-on:click="countup">
                                Add to Cart
                            </button>
                            <button class="button" v-on:click="countdown">
                                Delete to Cart
                            </button>
                        </div>
                    </div>
                </div>
            </article>
        </section>
    </div>
</template>

<script>
export default {
    data() {
        return {
            count: [],
            socksimage : '양말 이미지',
            num: 0,
            pic: require("../assets/img/socks_green.jpg"),
            productname: "Socks",
            list: ["50% cotton", "30% wool", "20% poltester"],
            products: [
                {
                    id: 1001,
                    color: "blue",
                    image: require("../assets/img/socks_blue.jpg"),
                },
                {
                    id: 1002,
                    color: "green",
                    image: require("../assets/img/socks_green.jpg"),
                },
            ],
        };
    },
    methods: {
        countup() {
            this.count.push(this.products[this.num].id);
        },
        countdown() {
            let num = this.count.indexOf(this.products[this.num].id);
            this.count.splice(num, 1);
        },
        change(index) {
            this.pic = this.products[index].image;
            this.num = index;
        },
    },
};
</script>

<style lang="scss" scoped>
@import "../assets/css/socks.scss";
</style>

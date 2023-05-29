<template>
    <div class="max-w-6xl mx-auto  px-[2%] my-5 relative">
        <div class="border bg-white md:shadow-md">
            <ul class="flex md:gap-x-10 p-5 py-0 justify-between">
                <li v-for="(e, index) in NoticeNav" :key="e" @click="TabSelectIndex = index" :class="TabSelectIndex === index && 'font-bold bg-[#0088cc] text-white'" class="basis-[20%] md:basis-[15%] text-xs sm:text-sm md:text-base py-5 text-center transition-all duration-500 rounded-br-2xl rounded-bl-2xl">
                    <a href="#" @click.prevent>{{ e }}</a>
                    <!-- a태그 쓰면서 위로 안올라가게 설정 @click.prevent -->
                </li>
            </ul>
            <div class="flex justify-between px-5 mt-4">
                <ul v-for="(e, index) in NoticeTabContent" :key="index" class="first-of-type:overflow-hidden first-of-type:mr-4 sm:mr-0">
                    <li v-for="(el, i) in e" :key="i" class="py-5 last-of-type:mb-3 text-xs sm:text-sm md:text-base">
                        <a href="#" @click.prevent class="flex flex-wrap items-center">
                            <!-- 아이콘 수정 -->
                            <img v-if="index === 0" :src="require(`@/assets/images/icon_water.png`)" alt="아이콘" class="h-full mr-3 hidden sm:inline-block">
                            <span class="overflow-hidden text-ellipsis whitespace-nowrap">{{ el }}</span>
                            <!-- ...쓸려면 저거 3개 다 써야됨 -->
                        </a>
                    </li>
                </ul>
            </div>
        </div>
    </div>
</template>

<script>

import NoticeData from "../assets/Data.json"

export default {
    name: "NoticePage",
    data() {
        return {
            NoticeNav: NoticeData.Notice.Nav,
            NoticeContent: NoticeData.Notice.Content,
            TabSelectIndex: 0
        }
    },
    computed: {
        NoticeTabContent(){
            // return console.log("A")
            return this.NoticeContent[`Notice_${this.TabSelectIndex}`].filter(data => data)
            // 오브젝트의 경우 배열로 이름을 출력

            // return this.Noticecontent[`Notice_${this.TabSelectIndex}`].filters((data)=>{
            //     return data
            // })
            // return console.log(this.NoticeContent["Noteice_1"])
        }
    },

    
}

</script>

<style >
    
</style>
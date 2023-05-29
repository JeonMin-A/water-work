<template>
    <div class="relative">
        <img :src="require(`@/assets/images/main_bg.png`)" alt="메인배경" class="absolute top-0 w-full h-full lg:h-auto sm:h-2/4">
        <div class="max-w-6xl mx-auto px-[2%]">
            <div class="w-full h-20 md:h-72 sm:h-96 flex sm:visible invisible relative justify-center items-center">
                <div class="relative w-3/5 md:w-3/5 lg:w-2/4">
                    <input type="text" placeholder="검색어를 입력해주세요." class="w-full border text-[#287bd1] placeholder:text-[#287bd1] border-[#287bd1] rounded-2xl p-3 text-sm font-bold">
                    <img :src="require(`@/assets/images/icon_search_blue.png`)" alt="검색" class="absolute top-3 right-3 inline-block cursor-pointer w-6 m-0">
                </div>
            </div>
            <!--  
                바로가기 메뉴 (자주 찾는 서비스)
            -->
            <div class="text-center font-bold relative text-2xl">
                <h3 class="font-extrabold">자주 찾는 서비스</h3>
                <div class="bg-white my-6 rounded-md border sm:shadow-md">
                    <ul class="flex flex-wrap justify-around my-5 transition-all duration-75">
                        <li v-for="(e, index) in Service" :key="e" class="py-4 text-center basis-1/4 lg:basis-auto">
                            <img :src="require(`@/assets/images/fav_0${index+1}.png`)" :alt="e" :title="e" class="mx-auto">
                            <!-- 
                                fav_0${index+1}.png >>> 1~8까지 순서대로 바인딩 한다는 뜻
                                
                                원래 textalign-center하면 둘다 정중앙으로 오는데 테일윈드에서는 이미지만 적용이 안되서 따로 적용 해줘야됨.
                            -->
                            <p class="text-xs sm:text-sm mt-4">{{ e }}</p>
                        </li>
                    </ul>                    
                </div>
                <div class="w-full">
                    <ul class="flex justify-between flex-wrap">
                        <li v-for="(e, index) in ServiceMenu" :key="e" class="h-32 basis-full mb-5 sm:mb-0 sm:basis-[32%] bg-white border rounded-tl-2xl rounded-br-2xl md:shadow-md">
                            <a href="#" class="flex items-center py-5 h-full">
                                <img :src="require(`@/assets/images/menu_0${index+1}.png`)" :alt="e" :title="e" class="mx-auto w-16">
                                <p class="text-base md:text-xl mt-4 basis-8/12">{{ e }}</p>
                            </a>
                        </li>
                    </ul>
                </div>
            </div>
            <!--  
                바로가기 메뉴 (자주 찾는 서비스)
            -->
        </div>
    </div>
</template>

<script>
import ServiceData from '../assets/Data.json'

export default {
    name: "MainPage",
    data() {
        return {
            Service: ServiceData.Service,
            ServiceMenu: ServiceData.ServiceMenu
            // 작명 할 때 걍 편하게 뒤에 이름이랑 똑같이 작명
        }
    },
}
</script>

<style>
    
</style>
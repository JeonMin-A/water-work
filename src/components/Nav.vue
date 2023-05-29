<template>
    <div class="w-full border-b h-20">
    
        <div class="max-w-7xl mx-auto h-full flex items-center">
    
            <!-- 로고 -->
    
            <div class="w-64 md:ml-8 absolute lg:static left-2/4 -translate-x-2/4 lg:left-0 lg:translate-x-0 flex items-center">
    
                <img :src="require(`@/assets/images/logo_img.png`)" alt="로고" class="ml-1 w-full">
    
                <img :src="require(`@/assets/images/logo.png`)" alt="로고" class="ml-1 w-full">
    
            </div>
    
            <!-- 로고 -->
    
            <!-- 네비 -->
            <div class="ml-20">
                <ul class=" hidden lg:flex font-bold text-lg">
                    <!-- <li class=" shrink-0
                        hover:text-[#37a2d7] h-20 leading-[80px] transition-all relative
                        after:absolute after:transition-all after:w-full after:h-0 after:bg-[#37a2d7] after:left-0 after:bottom-1 hover:after:h-1
                            " v-for="(e, index) in NavList" :key="e" :class="NavselectIndex == index && 'after:h-1 text-[#37a2d7]'" @mouseout="NavselectIndex = null"><a href="#">{{ e }}</a>
                    </li> -->
                    <li class=" xl:px-8 lg:px-5 shrink-0 h-20 leading-[80px] transition-all relative after:absolute after:transition-all after:w-full after:h-0 after:bg-[#37a2d7] after:left-0 after:bottom-1 hover:after:h-1" v-for="(e, index) in NavList" :key="e" :class="NavselectIndex == index && 'after:h-1 text-[#37a2d7]'" @mouseout="NavselectIndex = null" @mouseover="NavselectIndex = index; SubMenu(index)">
                        <a href="#">{{ e }}</a>
                        <ul class="absolute z-10 flex flex-wrap bg-white rounded-br-2xl rounded-bl-2xl -ml-5 transition-all duration-300 h-0 overflow-hidden" :style="NavselectIndex == index && isSubMenu">
                            <!-- 테일윈드에서 안먹어서 직접적으로 주는거 -->
                            <template v-for="el in SubList[index-1]" :key="el">
                                <li v-if="index != 0" class="text-xs shrink-0 basis-full text-center pt-5 last-of-type:pb-5">
                                    <a href="#" @click.prevent class="text-black hover:text-[#37a2d7]">{{ el }}</a>
                                </li>
                            </template>
                        </ul>
                    </li>
                </ul>
            </div>
    
            <!-- 반응형 네비 -->
            <div class=" lg:ml-20 w-6 h-6 hidden sm:hidden md:block cursor-pointer">
                <img :src="require(`@/assets/images/icon_lan.png`)" alt="언어변경" class="w-full">
            </div>
            <div class="w-6 h-6 -ml-10 block sm:block md:hidden">
                <img :src="require(`@/assets/images/icon_search.png`)" alt="검색" class="w-full">
            </div>
            <!-- 반응형 네비 -->
        </div>
    </div>
    <!--
        헤더 
    -->
    <!-- 햄버거 -->
    <div class="absolute right-4 md:right-8 top-6 duration-1000 transition-all z-50 cursor-pointer lg:hidden" @click="isOpen == true ? isOpen = false : isOpen = true" :class="isOpen && 'on'">
        <div v-for="e in 3" :key="e" class="w-[30px] h-0.5 bg-black rounded m-1.5 transition-all duration-1000"></div>
        <!-- <div class="w-6 h-0.5 bg-black rounded m-1.5 transition-all duration-1000"></div>
        <div class="w-6 h-0.5 bg-black rounded m-1.5 transition-all duration-1000"></div> -->
    </div>
    <div class="w-80 h-full fixed bg-gray-100 z-40 -right-80 p-12 box-border transition-all duration-500 top-0 lg:hidden overflow-y-scroll" :class="isOpen && '!right-0'">
        <ul class="`mt-12">
            <li class="py-5 border-b" v-for="(e, index) in NavList" :key="e">
                <a href="#" class="font-bold" @click="NavselectIndex = index; SubMenu(index)">{{ e }}</a>
                <!-- v-for랑 v-if을 같이 쓰고 싶을때는 template으로 묶어서   -->
                <template v-for="(e, i) in SubList" :key="e">
                    <ul v-if="index === i + 1" class="pt-5 flex flex-wrap justify-between sub_list h-0 overflow-hidden transition-all duration-300" :style="NavselectIndex === index && 'height:116px'">
                        <!-- v-if="index === i + 1" >>> 사이버민원센터는 서브메뉴가 없기에 무시 -->
                        <li v-for="el in e" :key="el" class="basis-2/4 pt-2 text-xs hover:text-[#37a2d7]">
                            <a href="#">{{ el }}</a>
                        </li>
                    </ul>
                </template>
            </li>
        </ul>
    </div>
    <!-- 바인딩 클래스에서 right-0 하면 안먹혀서  임포턴트 -->
    <!-- 햄버거 -->



</template>

<script>
import NavData from '../assets/Data.json'
export default {
    name: "NavPage",
    data() {
        return {
            NavList: NavData.Nav,
            SubList: NavData.SubMenu,
            SubMenuOpen: false,
            NavselectIndex: null,
            isOpen: false,
            isSubMenu: ''
        }
    },
    methods: {
        SubMenu(e){
            if( e != 0){
                const list = document.querySelectorAll(".sub_list")[e-1];
                const length = list.querySelectorAll("li").length;
                console.log(length)

                this.isSubMenu = `height:${length*52}px`; //세로길이값

                if(list.style.height === '0px'){
                    list.style.height = '116px';
                }else{
                    list.style.height = '0px';
                }
            }
        }
    },
}
</script>

<style>
    .on div:nth-child(1){
        transform: rotate(45deg) translateY(12px);
    }
    .on div:nth-child(2){
        opacity: 0;
        transform: translateX(-30px) rotate(720deg);
    }
    .on div:nth-child(3){
        transform: rotate(-45deg) translateY(-12px);
    }
</style>
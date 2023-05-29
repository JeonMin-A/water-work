<template>
    <div class="max-w-6xl mx-auto px-[2%] py-5">
        <div class="flex flex-wrap items-center justify-between">
            <!--  
                푸터 로고 영역
            -->
            <div class="basis-full md:basis-auto">
                <img :src="require(`@/assets/images/footer_logo.png`)" alt="로고" class="mx-auto">
            </div>
            <ul class="flex gap-x-5 mt-5 md:mt-0 justify-center basis-full md:basis-auto">
                <li v-for="e in FooterMenu" :key="e">
                    <a href="#" @click.prevent class="text-sm sm:text-sm md:text-base">{{ e }}</a>
                </li>
            </ul>
            <!--  
                주소, 번호 영역
            -->
            <ul class="flex text-xs sm:text-sm md:text-base flex-wrap basis-full justify-center text-gray-600 my-2">
                <li class="relative md:after:absolute after:w-0.5 after:h-2/4 after:bg-gray-600 after:-right-2 after:top-2/4 after:-translate-y-2/4 basis-full text-center md:basis-auto mr-2">(42423) 대구광역시 남구 명덕로54길 6-3 (이천동)</li>
                <li class="mr-2 md:ml-2 relative after:absolute after:w-0.5 after:h-2/4 after:bg-gray-600 after:-right-2 after:top-2/4 after:-translate-y-2/4">전화 053-670-2000</li>
                <li class="ml-1">팩스 053-670-2119</li>
            </ul>
            <!--  
                카피라이트 영역
            -->
            <p class="text-center basis-full text-xs sm:text-sm md:text-base text-gray-500">Copyright © Daegu Water. All rights Reserved </p>
        </div>
    </div>
</template>
<script>
export default {
    name: "FooterPage",
    data() {
        return {
            FooterMenu : ["개인정보처리방침", "법령정보", "뷰어프로그램"]
            // 간단한 데이터라면 임포트 없이 여기에다 작성해도 무관
        }
    },
}
</script>
<style>
    
</style>
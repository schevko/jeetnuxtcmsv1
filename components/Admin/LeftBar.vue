<template>
    
    <div class="p-4 border-r w-80">
        <div class="mb-8">
            <img class="w-40" src="/public/admin/img/jeetwork.svg" alt="">
        </div>

        <div>
            <ul class="p-3 pl-0">
                <li v-for="item in menuList" :key="item" class="p-2 mb-2 rounded rounded-lg bg-gray-100 transition-all hover:bg-black hover:text-white" >
                    {{ item.name }}
                </li>
            </ul>
        </div>

        <div>
            <Button size="small" label="Submit" />
        </div>
    </div>

</template>

<script setup>

    const menuList = [
        { name: "Anasayfa",url: "#",},
        { name: "Sayfalar",url: "#",},
        { name: "Hizmetler",url: "#",},
        { name: "Projeler",url: "#",},
        { name: "Blog Yazıları",url: "#",},
        { name: "Ürünler",url: "#",},
    ]

</script>
<script setup lang="ts">
defineProps({
  bookmark: {
    type: Object,
    required: true,
  },
})
const { t } = useI18n()
</script>

<template>
  <div class="mb-5 px-5 sm:px-0 js-header-anchor">
    <div class="relative flex items-center pl-20px h-44px h-bg font-bold h-border">
      <div class="absolute left-0 w-2px h-24px bg-green" />
      {{ bookmark.title }}
    </div>

    <div class="flex flex-wrap justify-between mx--2">
      <div v-for="(item, j) in bookmark.items" :key="j" class="flex-1 px-2 min-w-250px">
        <div class="flex flex-col mt-5 h-140px h-bg h-border transition-all hover:bg-gray1:80 dark:hover:bg-gray5:10 shadow">
          <a :href="item.zhLink || item.enLink" target="_blank" class="flex-1">
            <div class="px-14px py-10px">
              <div class="flex items-center">
                <SvgIcon v-if="item.icon" :name="item.icon" class="mr-10px w-40px h-40px" />
                <span class="ml-10px">{{ item.name }}</span>
              </div>
              <p class="line-clamp-2 mt-10px text-sm">
                {{ item.desc }}
              </p>
            </div>
          </a>
          <div class="flex items-center px-14px h-30px">
            <a v-if="item.github" class="icon-btn mr-2" :href="item.github" target="_blank">
              <div i-carbon-logo-github />
            </a>
            <a v-if="item.zhLink" class="badge-xs-green mr-2 hover:bg-green4:30" :href="item.zhLink" target="_blank">
              {{ t('button.zh_CN') }}
            </a>
            <a v-if="item.enLink" class="badge-xs-red mr-2 hover:bg-red4:30" :href="item.enLink" target="_blank">
              {{ t('button.english') }}
            </a>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

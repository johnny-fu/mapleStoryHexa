# 新楓之谷 六轉碎片計算器
由vue3 + vite + bootstrap5 撰寫  

計算六轉技能進度與計算累積打多少碎片

rwd 方便手機點選(應該ㄅ)

每日+每周、高山副本、公會城 碎片獎勵計算

!!以不缺靈魂方式計算

周王+活動靈魂愛爾達送蠻多的，應該不會缺

## Links

網頁地址 [六轉碎片計算器](https://johnny-fu.github.io/mapleStoryHexa/hexaSkill.html).
## 後續新增技能
在 skill.vue 底下  
const skill_core = ref([0])  
const proficient_core = ref([0])  
const strengthen_core = ref([0, 0, 0, 0])
const common_core = ref([0])
於陣列中新增 0 即可加該技能數量
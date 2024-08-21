<template>
    <div class="container">
        <img v-if="RogerSaidYouAre2486" src="../../../assets/2486.jpg">
        <img v-else-if="tureOrNot5555" src="../../../assets/5555.jpg">
        <img v-else-if="godton7414" src="../../../assets/7414.jpg">
        <img v-else class="img-thumbnail mb-3" src="../../../assets/newage.jpg">
        <div class="row">
            <div class="col-12 col-md-7 col-lg-7 border-end">
                <div v-for="(v, i) in skill_core" :key="i" class=" mb-1">
                    <div class="p-2">
                        <div class="mb-2">技能核心{{ i + 1 }}:</div>
                        <div class="row">
                            <div class="col-12 col-sm-6 col-md-5 mb-2">
                                <input type="range" class="form-range p-2" min="0" max="30" step="1" id="skill_core"
                                    v-model="skill_core[i]">
                            </div>
                            <div class="col-12 col-sm-6 col-md-7">
                                <input type="number" class="w-25" v-model="skill_core[i]" />
                            </div>
                        </div>
                    </div>
                </div>
                <div v-for="(v, i) in proficient_core" :key="i" class="mb-1">
                    <div class="p-2">
                        <div class="mb-2">精通核心{{ i + 1 }}:</div>
                        <div class="row">
                            <div class="col-12 col-sm-6 col-md-5 mb-2">
                                <input type="range" class="form-range p-2" min="0" max="30" step="1"
                                    id="proficient_core" v-model="proficient_core[i]">
                            </div>
                            <div class="col-12 col-sm-6 col-md-7">
                                <input type="number" class="w-25" v-model="proficient_core[i]" />
                            </div>
                        </div>
                    </div>
                </div>
                <div v-for="(v, i) in strengthen_core" :key="i" class="mb-1">
                    <div class="p-2">
                        <div class="mb-2"> 強化核心{{ i + 1 }}:</div>
                        <div class="row">
                            <div class="col-12 col-sm-6 col-md-5 mb-2">
                                <input type="range" class="form-range p-2" min="0" max="30" step="1"
                                    id="strengthen_core" v-model="strengthen_core[i]">
                            </div>
                            <div class="col-12 col-sm-6 col-md-7">
                                <input type="number" class="w-25" v-model="strengthen_core[i]" />
                            </div>
                        </div>
                    </div>
                </div>
                <div v-for="(v, i) in common_core" :key="i" class="mb-1">
                    <div class="p-2">
                        <div class="mb-2"> 共用核心{{ i + 1 }}:</div>
                        <div class="row">
                            <div class="col-12 col-sm-6 col-md-5 mb-2">
                                <input type="range" class="form-range p-2" min="0" max="30" step="1" id="common_core"
                                    v-model="common_core[i]">
                            </div>
                            <div class="col-12 col-sm-6 col-md-7">
                                <input type="number" class="w-25" v-model="common_core[i]" />
                            </div>
                        </div>
                    </div>
                </div>
                <button type="button" class="btn btn-danger" @click="clear">清空</button>
            </div>
            <div class="col-12 col-md-5 col-lg-5">
                <div class="p-3">
                    <div class="mb-2">
                        <div>
                            <img class="img" src="../../../assets/soul.png">靈魂愛爾達 : {{ soul }}
                        </div>
                    </div>
                    <div>
                        <img class="img" src="../../../assets/fragment.png">靈魂愛爾達碎片 : {{ fragments }}
                    </div>
                </div>
                <div class="p-3">
                    <div class="d-flex text-nowrap">
                        <!-- <div class="col"> -->
                        背包碎片 : &nbsp;
                        <!-- </div> -->
                        <!-- <div class="col"> -->
                        <input type="number" class="w-25" v-model="bag_fragment" />
                        <!-- </div> -->
                    </div>
                </div>
                <div class="p-3">
                    <div class="row mb-2">
                        <div class="col-12 col-lg-6 mb-2 text-nowrap">碎片進度 : {{ roundTo(progess, 2) }}%</div>
                        <div class="col-12 col-lg-6 text-nowrap">距離出獄還有 : {{
            remaining_daily != -1 ? Math.ceil(remaining_daily) + "天" : "遙遙無期" }}</div>
                    </div>
                    <div class="row">
                        <div class="form-check col-12 col-md-6 col-lg-4  mb-1">
                            <input class="form-check-input" type="checkbox" value="daily" id="dailyCheck"
                                v-model="otherfactor">
                            <label class="form-check-label" for="dailyCheck">
                                每日 + 每周
                            </label>
                        </div>
                        <div class="form-check col-12 col-md-6 col-lg-4 mb-1">
                            <input class="form-check-input" type="checkbox" value="dungeon" id="dungeonCheck"
                                v-model="otherfactor">
                            <label class="form-check-label" for="dungeonCheck">
                                高山副本
                            </label>
                            <div class="form-check">
                                <input class="form-check-input" type="radio" name="flexRadioDefault" value=0
                                    v-model="dungeon" id="flexRadioDefault1">
                                <label class="form-check-label" for="flexRadioDefault1">
                                    免費
                                </label>
                            </div>
                            <div class="form-check">
                                <input class="form-check-input" type="radio" name="flexRadioDefault" value=1
                                    v-model="dungeon" id="flexRadioDefault2">
                                <label class="form-check-label" for="flexRadioDefault2">
                                    200楓點
                                </label>
                            </div>
                            <div class="form-check">
                                <input class="form-check-input" type="radio" name="flexRadioDefault" value=2
                                    v-model="dungeon" id="flexRadioDefault3">
                                <label class="form-check-label" for="flexRadioDefault3">
                                    360楓點
                                </label>
                            </div>
                        </div>
                        <div class="form-check col-12 col-md-6 col-lg-4 mb-1">
                            <input class="form-check-input" type="checkbox" value="guild" id="guildCheck"
                                v-model="otherfactor">
                            <label class="form-check-label" for="guildCheck">
                                公會城
                            </label>
                            <div class="form-check">
                                <input class="form-check-input" type="radio" name="guildRadio" value=0 v-model="guild"
                                    id="guildRadio1">
                                <label class="form-check-label" for="guildRadio1">
                                    Lv.1
                                </label>
                            </div>
                            <div class="form-check">
                                <input class="form-check-input" type="radio" name="guildRadio" value=1 v-model="guild"
                                    id="guildRadio2">
                                <label class="form-check-label" for="guildRadio2">
                                    Lv.2
                                </label>
                            </div>
                            <div class="form-check">
                                <input class="form-check-input" type="radio" name="guildRadio" value=2 v-model="guild"
                                    id="guildRadio3">
                                <label class="form-check-label" for="guildRadio3">
                                    Lv.3
                                </label>
                            </div>
                            <div class="form-check">
                                <input class="form-check-input" type="radio" name="guildRadio" value=3 v-model="guild"
                                    id="guildRadio4">
                                <label class="form-check-label" for="guildRadio4">
                                    Lv.4
                                </label>
                            </div>
                            <div class="form-check">
                                <input class="form-check-input" type="radio" name="guildRadio" value=4 v-model="guild"
                                    id="guildRadio5">
                                <label class="form-check-label" for="guildRadio5">
                                    Lv.5
                                </label>
                            </div>
                        </div>
                    </div>
                </div>
                <div>備註:</div>
                <div class="text-danger">公會城的碎片取最多能獲得量，請相信自己是歐洲人</div>
                <div class="text-danger">!!出獄進度以不缺靈魂方式計算</div>
                <div class="text-danger">!!出獄進度以不缺靈魂方式計算</div>
                <div class="text-danger">!!出獄進度以不缺靈魂方式計算</div>
            </div>
        </div>
    </div>

</template>

<script setup>
import { onMounted, ref, watch } from "vue";
const skill_core_fragments = [0, 30, 35, 40, 45, 50, 55, 60, 65, 200, 80, 90, 100, 110, 120, 130, 140, 150, 160, 350, 170, 180, 190, 200, 210, 220, 230, 240, 250, 500]
const skill_core_soul = [0, 1, 1, 1, 2, 2, 2, 3, 3, 10, 3, 3, 4, 4, 4, 4, 4, 4, 5, 15, 5, 5, 5, 5, 5, 6, 6, 6, 7, 20]
const proficient_core_fragments = [50, 15, 18, 20, 23, 25, 28, 30, 33, 100, 40, 45, 50, 55, 60, 65, 70, 75, 80, 175, 85, 90, 95, 100, 105, 110, 115, 120, 125, 250]
const proficient_core_soul = [3, 1, 1, 1, 1, 1, 1, 2, 2, 5, 2, 2, 2, 2, 2, 2, 2, 2, 3, 8, 3, 3, 3, 3, 3, 3, 3, 3, 3, 10]
const strengthen_core_fragments = [75, 23, 27, 30, 34, 38, 42, 45, 49, 150, 60, 68, 75, 83, 90, 98, 105, 113, 120, 263, 128, 135, 143, 150, 158, 165, 173, 180, 188, 375]
const strengthen_core_soul = [4, 1, 1, 1, 2, 2, 2, 3, 3, 8, 3, 3, 3, 3, 3, 3, 3, 3, 4, 12, 4, 4, 4, 4, 4, 5, 5, 5, 6, 15]
const common_core_fragments = [125, 38, 44, 50, 57, 63, 69, 75, 82, 300, 110, 124, 138, 152, 165, 179, 193, 207, 220, 525, 234, 248, 262, 275, 289, 303, 317, 330, 344, 750]
const commo_core_soul = [7, 2, 2, 2, 3, 3, 3, 5, 5, 14, 5, 5, 6, 6, 6, 6, 6, 6, 7, 17, 7, 7, 7, 7, 7, 9, 9, 9, 10, 20]
const dungeon_fragments = [30, 90, 150]
const guild_fragments = [23, 26, 29, 32, 35]

const skill_core = ref([0])
const proficient_core = ref([0,0])
const strengthen_core = ref([0, 0, 0, 0])
const common_core = ref([0])
const fragments = ref(0)
const soul = ref(0)
const progess = ref(0)
const bag_fragment = ref(0)
const remaining_daily = ref(0)
const otherfactor = ref(["daily"])
const dungeon = ref(0)
const guild = ref(0)

var all_fragment = 0
var all_soul = 0

//不重要
const RogerSaidYouAre2486 = ref(false)
const tureOrNot5555 = ref(false)
const godton7414 = ref(false)
//



function count() {
    fragments.value = 0
    soul.value = 0
    skill_core.value.forEach(num => {
        if (num < 0) {
        } else if (num > 30) {
            countSkill(30)
        } else {
            countSkill(num)
        }
    });
    proficient_core.value.forEach(num => {
        if (num < 0) {
        } else if (num > 30) {
            countProficient(30)
        } else {
            countProficient(num)
        }
    });
    strengthen_core.value.forEach(num => {
        if (num < 0) {
        } else if (num > 30) {
            countStrengthen(30)
        } else {
            countStrengthen(num)
        }
    });
    common_core.value.forEach(num => {
        if (num < 0) {
        } else if (num > 30) {
            countCommon(30)
        } else {
            countCommon(num)
        }
    });
}
function countSkill(x) {
    for (var i = 0; i < x; i++) {
        fragments.value = fragments.value + skill_core_fragments[i];
        soul.value = soul.value + skill_core_soul[i];
    }
}
function countProficient(x) {
    for (var i = 0; i < x; i++) {
        fragments.value = fragments.value + proficient_core_fragments[i];
        soul.value = soul.value + proficient_core_soul[i];
    }
}
function countStrengthen(x) {
    for (var i = 0; i < x; i++) {
        fragments.value = fragments.value + strengthen_core_fragments[i];
        soul.value = soul.value + strengthen_core_soul[i];
    }
}
function countCommon(x) {
    for (var i = 0; i < x; i++) {
        fragments.value = fragments.value + common_core_fragments[i];
        soul.value = soul.value + commo_core_soul[i];
    }
}

function countDailyAndProgess() {
    var tempBagFragment = 0;
    var remainingDay = 0;
    var remaining = 0;

    if (bag_fragment.value > 0) {
        tempBagFragment = bag_fragment.value
    }
    remaining = all_fragment - (fragments.value + tempBagFragment)

    if (otherfactor.value.length == 0) {
        remainingDay = -1
    } else {
        remainingDay = calremainingDay(remaining)
    }

    //返回剩餘天數 與 進度
    remaining_daily.value = remainingDay

    progess.value = (fragments.value + tempBagFragment) / all_fragment * 100
    if (progess.value > 100) {
        progess.value = 100
    }
}

function calremainingDay(remaining) {
    var remainingDay = 0;
    var date = new Date().getDay();
    var weekcomplete = false
    var dungeoncomplete = false
    var guildcomplete = false
    //計算剩餘天數
    //以 剩餘需要碎片 - 每日 
    //剩餘需要碎片 - 每周 - 高山 
    while (remaining > 0) {
        remainingDay++

        if (otherfactor.value.includes('daily')) {
            remaining = remaining - 12
            if (date >= 3 && !weekcomplete) {
                remaining = remaining - 50
                weekcomplete = true
            }
        }
        if (otherfactor.value.includes('dungeon')) {

            if (!dungeoncomplete) {
                remaining = remaining - dungeon_fragments[dungeon.value]
                dungeoncomplete = true
            }
        }
        if (otherfactor.value.includes('guild')) {
            if (!guildcomplete) {
                remaining = remaining - guild_fragments[guild.value]
                guildcomplete = true
            }
        }
        date++
        if (date == 7) {
            date = 0
            weekcomplete = false
            guildcomplete = false
        }
        if (date == 3) {
            dungeoncomplete = false
        }
    }
    return remainingDay
}

function checkAll() {
    fragments.value = 0
    soul.value = 0
    skill_core.value.forEach(num => {
        countSkill(30)
    });
    proficient_core.value.forEach(num => {
        countProficient(30)
    });
    strengthen_core.value.forEach(num => {
        countStrengthen(30)
    });
    common_core.value.forEach(num => {
        countCommon(30)
    });
    all_fragment = fragments.value
    all_soul = soul.value
    fragments.value = 0
    soul.value = 0
}

function clear() {
    fragments.value = 0
    soul.value = 0
    for (var i = 0; i < skill_core.value.length; i++) {
        skill_core.value[i] = 0
    }
    for (var i = 0; i < proficient_core.value.length; i++) {
        proficient_core.value[i] = 0
    }
    for (var i = 0; i < strengthen_core.value.length; i++) {
        strengthen_core.value[i] = 0
    }
    for (var i = 0; i < common_core.value.length; i++) {
        common_core.value[i] = 0
    }
    otherfactor.value = []
    dungeon.value = 0
    guild.value = 0
}

const roundTo = function (num, decimal) { return Math.round((num + Number.EPSILON) * Math.pow(10, decimal)) / Math.pow(10, decimal); }
watch([skill_core.value, proficient_core.value, strengthen_core.value, common_core.value], async (newVal, oldVal) => {
    count()
    countDailyAndProgess()
})
watch(bag_fragment, () => {
    countDailyAndProgess()
    switch (bag_fragment.value) {
        case 2486:
            RogerSaidYouAre2486.value = true
            break
        case 555:
            tureOrNot5555.value = true
            break
        case 7414:
            godton7414.value = true
            break
        default:
            RogerSaidYouAre2486.value = false
            tureOrNot5555.value = false
            godton7414.value = false
            break
    }
    
})
watch(otherfactor, () => {
    countDailyAndProgess()
})
watch(dungeon, () => {
    countDailyAndProgess()
})
watch(guild, () => {
    countDailyAndProgess()
})
onMounted(() => {
    checkAll()
    countDailyAndProgess()
})
</script>

<style scoped></style>
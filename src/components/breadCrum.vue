<script>
import { RouterLink } from 'vue-router'
export default {
    components: {
        RouterLink
    },
    data(){
        return{
            breadCrumList:[icon:'../public/HomeIcon.svg']
        }
    },
    mounted () { this.updateList() },
    watch: {'$route'(){ this.updateList() }},
    methods:{
        routeTo (index){
            if(this.breadCrumList[index].link) this.$router.push(this.breadCrumList[index].link)
        },
        updateList(){this.breadCrumList = this.$route.meta.breadCrum}
        }
    
}
</script>

<template>
    <div class="breadCrum">
        <ul>
            <li
            v-for="(breadCrum, index) in breadCrumList"
            :key="index"
            @click="routeTo(index)"
            :class="{'linked': !!breadCrum.link}">
            {{ breadCrum.name }}{{ breadCrum.icon }}
            </li>
        </ul>
    </div>
</template>

<style scoped lang="scss">
*{
    margin: 0;
    padding: 0;
}
.breadCrum {
    border-bottom:2px solid #39AB4B;
    width: 100dvw;
    height: 35px;
    ul{
        display: flex;
        list-style: none;
        // font-size: font(1);
        margin-left: 20px;
        align-items: center;
    }
    li{
        cursor: pointer;
        color: #39AB4B;
        font-size: 20px;
        margin-left: 15px;
    }
    li:not(:last-child):after{
        content: ">>";
        margin-left: 10px;
    }
}
</style>
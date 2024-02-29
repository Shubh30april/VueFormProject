<template>
    <div class="row">
        <div class="grid-container">
        <div class="column" v-for="(item, index) in items" :key="index">
            <div class="card">
                <div class="header">
                    <div class="name" :title="item.fname">
                        Name : {{ item.fname }}
                    </div> 
                    <div class="acstatusClass" :class="{'active':item.acstatus==='Active','inactive':item.acstatus==='Inactive'}">
                        {{ item.acstatus }}
                    </div>
                </div>
                <div class="genderClass">Gender: {{ item.picked }}</div>
                <div class="companyClass">Comapany: {{ item.company }}</div>
                <div class="birthdayClass">Birthday: {{ item.birthday }}</div>

                <br><br>
            </div>
            </div>
        </div>
    </div>
</template>
<script setup>
import { ref } from "vue";


const props = defineProps({
    items: {
        type: Array,
        required: true
    },
})
</script>

<style scoped>
.column {
    width: 280px;
    padding: 10px;    
}
.grid-container{
    display: grid;
    grid-template-columns: auto auto auto auto;
    padding: 1px;
}

.row {
    margin: 20px 10px;
}

.row:after {
    content: "";
    display: table;
    clear: both;
}

.card {
    box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2);
    background-color: white;
    border: 2px solid black;

}
.name{
    width: 150px;
    white-space: nowrap;
    overflow: hidden;
    text-overflow: ellipsis;
}
.name:hover {
    /* overflow: visible; */
    /* white-space: normal; */
    cursor:default;
}
.header {
    background-color: black;
    text-align: left;
    color: white;
    display: flex;
    padding: 10px;
    min-width: 23%;



    
}

.acstatusClass {
    width: fit-content;
    /* margin-left: auto; 
    margin-right: 0; */
    position: relative;
    left: 60px;

}

.genderClass {
    padding: 10px;
}

.companyClass {
    padding: 10px;
}
.birthdayClass{
    padding: 10px;
}


.active {
    background-color: green;
}

.inactive {
    background-color: red;
}

</style>


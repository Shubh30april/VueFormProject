<template>
    <headTop></headTop>
    <div class="inp card">
        <form @submit.prevent="addItem" class="formTag">
            <div id="nameField">
                <label for="name">Name: </label>
                <input type="text" style="padding-bottom: 5px" v-model="newInfo.fname" />
                <br />
            </div>
            <div id="genderField">
                <label for="">Gender:</label>
                <input type="radio" id="Male" value="Male" v-model="newInfo.picked" />
                <label for="Male">Male</label>
                <input type="radio" id="Female" value="Female" v-model="newInfo.picked" />
                <label for="Female">Female</label>
            </div>
            <div id="statusField">
                <label for="">Status:</label>
                <input type="radio" id="Active" value="Active" v-model="newInfo.acstatus" />
                <label for="Active">Active</label>
                <input type="radio" id="Inactive" value="Inactive" v-model="newInfo.acstatus" />
                <label for="Inactive">Inactive</label>
                <br />
            </div>
            <div class="company">
                <label for="company">Company: </label>
                <select v-model="newInfo.company" name="company" id="company">
                <option value="MBRDI">MBRDI</option>
                <option value="Capegemini">Capegemini</option>
                <option value="IBM">IBM</option>
                </select>
            </div>
            <div class="birthday">
                <label for="birthday">Birthday:</label>
                <input type="date" id="birthday" name="birthday" v-model="newInfo.birthday">
            </div>
            <input type="submit" class="sub-btn" />
        </form>
    </div>
    <TableComp :items="items"></TableComp>
</template>
<script setup>

import { ref } from "vue";
import TableComp from "./table-comp.vue";
import headTop from "./head-top.vue";

const newInfo = ref({
    fname: "",
    picked: "",
    acstatus: "",
    company:"",
    birthday:""
});
const items = ref([]);

function addItem() {
    items.value.push({ ...newInfo.value });
    newInfo.value.fname = "";
    newInfo.value.picked = "";
    newInfo.value.acstatus = "";
    newInfo.value.company="";
    newInfo.value.birthday="";
}
</script>

<style scoped>
.inp {
    box-shadow: 10px;
    padding-top: 40px;
    width: 300px;
    top: 0;
    bottom: 0;
    left: 0;
    right: 0;
    margin: auto;
    margin-top: 80px;

}

.card {
    box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2);
    padding: 16px;
    background-color: white;
    border: 2px solid black;
    position: relative;

}

.formTag {
    height: 200px;
    display: flex;
    flex-direction: column;
    justify-content: space-evenly;
    padding: 10px;
    
}

.sub-btn {
    background-color: #0066ff;
    padding: 5px;
    width: 100px;
    color: white;
}</style>

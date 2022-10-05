<script setup>
import { ref } from 'vue'

const profileName = ref(null)
const profile = ref(null)

const fetchProfile = () => {
    fetch(`http://timoth.yt/api/rampup?name=${profileName.value}`, {
        method: 'GET',
        headers: {
            'Content-Type': 'application/json',
        },
    })
    .then(response => response.json())
    .then(data => profile.value = data)
}

/* ADD JAVASCRIPT CODE HERE */

const editProfileName = () => {
    console.log(profile.Age.value);
    let new_body = {
        'Name': profile.Name.value,
        'Age': profile.Age.value,
        'Bio': profile.Bio.value,
        'Likes': profile.Likes,
        'Link': profile.Link.value,
    }

    fetch(`http://timoth.yt/api/rampup?name=${profile.Name.value}`, {
        method: 'POST',
        headers: {
            'Content-Type': 'application/json',
        },
        body: JSON.stringify(new_body)
    })

}


</script>

<template>
    <h1>Edit Profile</h1>
    <form id="fetchProfileForm" onsubmit="return false">
        <label for="profileName">Profile Name:</label>
        <input id="profileName" v-model="profileName" required>
        <input type="submit" @click="fetchProfile()">
    </form>
    <div v-if="profile">
        <form onsubmit="return false">
        <input id="name" v-model="profile.Name" placeholder="First Name">
        <input id="age" v-model="profile.Age" placeholder="First Name">
        <input id="bio" v-model="profile.Bio" placeholder="First Name">
        <!-- <div v-for="(item, index) in profile.Likes" :key="item.id">
            {{index}}: {{item}}
        </div> -->
        <input id="link" v-model="profile.Link" placeholder="First Name">
        <input type="submit" @click="editProfileName()">
        </form>
    </div>


</template>

<style scoped>

#fetchProfileForm input {
    margin: 5px;
    background-color: #d1d1d1;
    border-radius: 5px;
}

.sub-form {
    width: 100%;
    display: flex;
    flex-direction: row;
}

.pair {
    display: flex;
    flex-direction: column;
}

.pair input {
    min-width: 250px;
}
</style>

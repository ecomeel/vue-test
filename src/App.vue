<template>
    <div class="app">
        <form @submit.prevent>
            <input
                class="input"
                type="text"
                placeholder="title"
                @input="title = $event.target.value"
                v-bind:value="title"
            />
            <input
                class="input"
                type="text"
                placeholder="description"
                @input="body = $event.target.value"
                v-bind:value="body"
            />
            <button class="btn" @click="createPost">Create post</button>
        </form>
        <div class="post" v-for="post in posts">
            <div><strong>Название:</strong>{{ post.title }}</div>
            <div><strong>Описание:</strong>{{ post.body }}</div>
        </div>
    </div>
</template>
<script>
export default {
    data() {
        return {
            posts: [
                { id: 1, title: "Javascript", body: "Description" },
                { id: 2, title: "Javascript2", body: "Description2" },
                { id: 3, title: "Javascript3", body: "Description3" },
                { id: 4, title: "Javascript3", body: "Description3" },
            ],
            title: "",
            body: "",
        };
    },
    methods: {
        createPost(e) {
            // e.stopPropagation()
            // e.preventDefault()
            const newPost = {
                id: new Date(),
                title: this.title,
                body: this.body,
            };
            this.posts.push(newPost);
            this.title = "";
            this.body = "";
        },
    },
};
</script>
<style>
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}
.app {
    padding: 15px;
}
.post {
    margin-top: 15px;
    padding: 15px;
    border: 2px solid green;
}
form {
    display: flex;
    flex-direction: column;
}
.btn {
    margin-top: 15px;
    padding: 10px 15px;
    align-self: flex-end;
    background: none;
    border: 2px solid green;
    color: teal;
}
.input {
    margin-top: 15px;
    padding: 10px 15px;
    width: 100%;
    border: 2px solid green;
}
</style>

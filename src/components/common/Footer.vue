<template>
    <div class="footer">
        <ul>
            <li v-for="(msg, index) in msg_list" :key="index">
                <span v-if="msg.is_site=1"><a :href="msg.link">{{ msg.title }}</a></span>
                <span v-else><router-link :to="msg.link">{{ msg.title }}</router-link></span>
            </li>
        </ul>
    </div>
</template>

<script>
export default {
    name: "Footer",
    data() {
        return {
            msg_list: []
        }
    },
    methods: {
        get_all_message() {
            this.$axios.get(this.$settings.HOST + 'home/navigation_f/').then(response => {
                this.msg_list = response.data;
            })
        }
    },
    created() {
        this.get_all_message();
    }
}
</script>

<style scoped>
.footer {
    width: 100%;
    height: 128px;
    background: #25292e;
    color: #fff;
}

.footer ul {
    margin: 0 auto 16px;
    padding-top: 38px;
    width: 810px;
}

.footer ul li {
    float: left;
    width: 112px;
    margin: 0 10px;
    text-align: center;
    font-size: 14px;
}

.footer ul::after {
    content: "";
    display: block;
    clear: both;
}

.footer p {
    text-align: center;
    font-size: 12px;
}

.footer a {
    color: #fff;
}
</style>

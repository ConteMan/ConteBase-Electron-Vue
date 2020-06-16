<template>
    <div>
        <meta name="referrer" content="no-referrer">
        <div class="sider">
        </div>
        <div class="title">
        </div>
        <div class="detail">
        </div>
    </div>
</template>

<script>
    import { mapGetters } from "vuex"

    export default {
        name: "index",
        data() {
            return {}
        },
        computed: {
            ...mapGetters(
                {
                    baseList: 'baseList'
                }
            )
        },
        async mounted() {
        },
        methods: {
        }
    }
</script>

<style lang="less" scoped>
        .sider,.title,.detail {
            display: inline-block;
            height: 100%;
        }
        .title {
            overflow-y: scroll;
        }
        .sider {
            position: fixed;
            background: #828282;
            width: 200px;
        }
        .title {
            position: fixed;
            margin-left: 200px;
            background: #F7F6F3;
            width: 260px;
        }
        .detail {
            margin-left: 460px;
            padding: 10px 20px;
            width: calc(100% - 460px);
            display: flex;
            flex-direction: row;
            justify-content: center;
            /deep/ #js_content {
                visibility: visible !important;
            }
            /deep/ img {
                max-width: 100%;
            }
        }
        .detail > div {
            max-width: 850px;
        }
</style>
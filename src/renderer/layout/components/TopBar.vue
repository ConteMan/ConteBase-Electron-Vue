<template>
    <div class="header">
        <div class="logo">Base Electron Vue</div>
        <div class="operate">
            <div class="item">
                <i class="bev-family bev-code"></i>
            </div>
            <div class="item">
                <i class="bev-family bev-good"></i>
            </div>
            <div class="item">
                <i class="bev-family bev-jewelry"></i>
            </div>
        </div>
        <div class="tool">
            <div class="item" @click="winControl('minimize')">
                <i class="bev-family bev-zuixiaohua"></i>
            </div>
            <div class="item" @click="winControl('maximize')">
                <i class="bev-family bev-zuidahua"></i>
            </div>
            <div class="item" @click="winControl('close')">
                <i class="bev-family bev-guanbi"></i>
            </div>
        </div>
    </div>
</template>

<script>
    const electron = require('electron');
    const { remote } = electron;

    export default {
        name: "TopBar",
        data() {
            return {
            }
        },
        computed: {
        },
        methods: {
            winControl(action) {
                const browserWindow = remote.getCurrentWindow()
                switch (action) {
                    case 'minimize':
                        browserWindow.minimize()
                        break;
                    case 'maximize':
                        if (browserWindow.isMaximized()) {
                            browserWindow.unmaximize()
                        } else {
                            if (this.isMaximized) {
                                browserWindow.unmaximize()
                            } else {
                                browserWindow.maximize()
                            }
                        }
                        this.isMaximized = !this.isMaximized
                        break;
                    case 'close':
                        browserWindow.close()
                        break;
                    default:
                        break;
                }
            }
        }
    }
</script>

<style lang="less" scoped>
    .header {
        position: absolute;
        top: 0;
        width: 100%;
        height: 50px;
        background: #4F4F4F;
        color: aliceblue;
        border-radius: 0;
        -webkit-app-region: drag;
        .logo {
            display: inline-block;
            width: 200px;
            height: 50px;
            line-height: 50px;
            font-size: 20px;
            font-weight: bold;
            text-align: center;
        }
        .operate {
            display: inline-block;
            width: 260px;
            text-align: center;
            .item {
                -webkit-app-region: no-drag;
                display: inline-block;
                cursor: pointer;
                margin-right: 20px;
                i {
                    font-size: 16px;
                }
            }
        }
        .tool {
            -webkit-app-region: no-drag;
            display: inline-block;
            float: right;
            padding: 12px 0 0 0;
            .item {
                -webkit-app-region: no-drag;
                display: inline-block;
                cursor: pointer;
                margin-right: 10px;
                i {
                    font-size: 14px;
                }
            }
        }
    }
</style>
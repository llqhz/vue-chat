<template>
    <div id="contact">
        <section>
            <div class="weui-cells_contact-head weui-cells weui-cells_access" style="margin-top:-1px">
                <router-link to="/contact/new-friends" class="weui-cell">
                    <div class="weui-cell_hd"> <img class="img-obj-cover" src="../../assets/images/contact_top-friend-notify.png"> </div>
                    <div class="weui-cell_bd weui-cell_primary">
                        <p>新的朋友</p>
                    </div>
                </router-link>
                <router-link to="/contact/group-list" class="weui-cell">
                    <div class="weui-cell_hd"> <img class="img-obj-cover" src="../../assets/images/contact_top-addgroup.png"> </div>
                    <div class="weui-cell_bd weui-cell_primary">
                        <p>群聊</p>
                    </div>
                </router-link>
                <router-link to="/contact/tags" class="weui-cell">
                    <div class="weui-cell_hd"> <img class="img-obj-cover" src="../../assets/images/contact_top-tag.png"> </div>
                    <div class="weui-cell_bd weui-cell_primary">
                        <p>标签</p>
                    </div>
                </router-link>
                <router-link to="/contact/official-accounts" class="weui-cell">
                    <div class="weui-cell_hd"><img class="img-obj-cover" src="../../assets/images/contact_top-offical.png"></div>
                    <div class="weui-cell_bd weui-cell_primary">
                        <p>公众号</p>
                    </div>
                </router-link>
            </div>
            <!--联系人集合-->
            <template v-for="(value,key) in contactsList">
                <!--首字母-->
                <div :ref="`key_${key}`" class="weui-cells__title">{{key}}</div>
                <div class="weui-cells">
                    <router-link :key="item.wxid" :to="{path:'/contact/details',query:{wxid:item.wxid}}" class="weui-cell weui-cell_access" v-for="item in value"
                        tag="div">
                        <div class="weui-cell__hd">
                            <img :src="item.headerUrl" class="home__mini-avatar___1nSrW">
                        </div>
                        <div class="weui-cell__bd">
                            {{item.remark?item.remark:item.nickname}}
                        </div>
                    </router-link>
                </div>
            </template>
</section>
<!--检索-->
<div class="initial-bar"><span @click="toPs(i)" v-for="i in contactsInitialList">{{i}}</span></div>
</div>
</template>
<script>
    export default {
        mixins: [window.mixin],
        data() {
            return {
                "pageName": "客服列表"
            }
        },
        mounted() {
            // mutations.js中有介绍
            this.$store.commit("toggleTipsStatus", -1)
        },
        activated() {
            this.$store.commit("toggleTipsStatus", -1)
        },
        computed: {
            contactsInitialList() {
                var list =  this.$store.getters.contactsInitialList
                console.log(list);
                return list;
                
            },
            contactsList() {
                var list =  this.$store.getters.contactsList
                //console.log(JSON.stringify(list,' ',4));
                var waiterLIst = 
                {
                    "B": [
                        {
                            "wxid": "wxid_xiaoguai",
                            "initial": "b",
                            "headerUrl": "http://thirdwx.qlogo.cn/mmopen/vi_32/rgmtJfdPRoianrDeicYkkl5Y9cukTMCzvD2McCcpJ7ZJK2y23yVgtISrSKUjNFPJvblNuZbSepkVvFCc42xzgKbg/0",
                            "nickname": "★筱 怪★",
                            "sex": 0,
                            "remark": "",
                            "signature": "筱怪不怪",
                            "telphone": 18896586152,
                            "album": [
                                {
                                    "imgSrc": "https://sinacloud.net/vue-wechat/images/album/baiqian/baiqian01.jpeg",
                                    "date": 182625262
                                },
                                {
                                    "imgSrc": "https://sinacloud.net/vue-wechat/images/album/baiqian/baiqian02.jpeg",
                                    "date": 182625262
                                }
                            ],
                            "area": [
                                "青丘",
                                "狐狸洞"
                            ],
                            "from": "通过扫一扫",
                            "tag": "女帝",
                            "desc": {
                                "title": "",
                                "picUrl": ""
                            }
                        },
                        {
                            "wxid": "wxid_baiqian",
                            "initial": "b",
                            "headerUrl": "https://sinacloud.net/vue-wechat/images/headers/baiqian.jpg",
                            "nickname": "白浅",
                            "sex": 0,
                            "remark": "",
                            "signature": "青丘女帝，天族天妃",
                            "telphone": 18896586152,
                            "album": [
                                {
                                    "imgSrc": "https://sinacloud.net/vue-wechat/images/album/baiqian/baiqian01.jpeg",
                                    "date": 182625262
                                },
                                {
                                    "imgSrc": "https://sinacloud.net/vue-wechat/images/album/baiqian/baiqian02.jpeg",
                                    "date": 182625262
                                }
                            ],
                            "area": [
                                "青丘",
                                "狐狸洞"
                            ],
                            "from": "通过扫一扫",
                            "tag": "女帝",
                            "desc": {
                                "title": "",
                                "picUrl": ""
                            }
                        }
                    ],
                    "G": [
                        {
                            "wxid": "wxid_guangyu",
                            "initial": "g",
                            "headerUrl": "https://sinacloud.net/vue-wechat/images/headers/guangyu.jpg",
                            "nickname": "关羽",
                            "sex": 1,
                            "remark": "关羽",
                            "signature": "观尔乃插标卖首",
                            "telphone": 18896586152,
                            "album": [
                                {
                                    "imgSrc": "https://sinacloud.net/vue-wechat/images/album/baiqian/baiqian02.jpeg",
                                    "date": 182625262
                                },
                                {
                                    "imgSrc": "https://sinacloud.net/vue-wechat/images/album/guanyu/guanyu01.jpeg",
                                    "date": 182625262
                                }
                            ],
                            "area": [
                                "蜀国",
                                "荆州"
                            ],
                            "from": "通过扫一扫",
                            "tag": "蜀",
                            "desc": {
                                "title": "",
                                "picUrl": ""
                            }
                        }
                    ],
                    "H": [
                        {
                            "wxid": "wxid_huangyueying",
                            "initial": "h",
                            "headerUrl": "https://sinacloud.net/vue-wechat/images/headers/huangyueying.jpg",
                            "nickname": "黄月英",
                            "sex": 0,
                            "remark": "黄月英",
                            "signature": "哼哼~",
                            "telphone": 18896586152,
                            "album": [
                                {
                                    "imgSrc": "https://sinacloud.net/vue-wechat/images/album/guanyu/guanyu02.jpeg",
                                    "date": 182625262
                                }
                            ],
                            "area": [
                                "蜀",
                                "荆州"
                            ],
                            "from": "通过手机号码添加",
                            "tag": "蜀",
                            "desc": {
                                "title": "",
                                "picUrl": ""
                            }
                        }
                    ],
                    "L": [
                        {
                            "wxid": "wxid_liubei",
                            "initial": "l",
                            "headerUrl": "https://sinacloud.net/vue-wechat/images/headers/liubei.jpg",
                            "nickname": "刘备",
                            "sex": 1,
                            "remark": "刘备",
                            "signature": "惟贤惟德，仁服于人",
                            "telphone": 18896586152,
                            "album": [
                                {
                                    "imgSrc": "https://sinacloud.net/vue-wechat/images/album/guanyu/guanyu02.jpeg",
                                    "date": 182625262
                                },
                                {
                                    "imgSrc": "https://sinacloud.net/vue-wechat/images/album/baiqian/baiqian01.jpeg",
                                    "date": 182625262
                                }
                            ],
                            "area": [
                                "蜀国",
                                "荆州"
                            ],
                            "from": "通过扫一扫",
                            "tag": "主公",
                            "desc": {
                                "title": "",
                                "picUrl": ""
                            }
                        }
                    ],
                    "S": [
                        {
                            "wxid": "wxid_sunshangxiang",
                            "initial": "s",
                            "headerUrl": "https://sinacloud.net/vue-wechat/images/headers/sunshangxiang.jpg",
                            "nickname": "孙尚香",
                            "sex": 0,
                            "remark": "孙尚香2",
                            "signature": "夫君,身体要紧~",
                            "telphone": 18896586152,
                            "album": [
                                {
                                    "imgSrc": "https://sinacloud.net/vue-wechat/images/album/baiqian/baiqian02.jpeg",
                                    "date": 182625262
                                }
                            ],
                            "area": [
                                "吴国",
                                "富春"
                            ],
                            "from": "通过手机号码添加",
                            "tag": "孙夫人",
                            "desc": {
                                "title": "",
                                "picUrl": ""
                            }
                        },
                        {
                            "wxid": "wxid_sunquan",
                            "initial": "s",
                            "headerUrl": "https://sinacloud.net/vue-wechat/images/headers/sunquan.jpg",
                            "nickname": "孙权",
                            "sex": 1,
                            "remark": "孙权",
                            "signature": "容我三思",
                            "telphone": 18896586152,
                            "album": [
                                {
                                    "imgSrc": "https://sinacloud.net/vue-wechat/images/album/guanyu/guanyu01.jpeg",
                                    "date": 182625262
                                }
                            ],
                            "area": [
                                "吴国",
                                "吴郡"
                            ],
                            "from": "通过手机号码添加",
                            "tag": "主公",
                            "desc": {
                                "title": "",
                                "picUrl": ""
                            }
                        }
                    ],
                    "Y": [
                        {
                            "wxid": "wxid_yehua",
                            "initial": "y",
                            "headerUrl": "https://sinacloud.net/vue-wechat/images/headers/yehua.jpg",
                            "nickname": "夜华",
                            "sex": 1,
                            "remark": "夜华",
                            "signature": "浅浅，过来",
                            "telphone": 18896586152,
                            "album": [
                                {
                                    "imgSrc": "https://sinacloud.net/vue-wechat/images/album/guanyu/guanyu02.jpeg",
                                    "date": 182625262
                                },
                                {
                                    "imgSrc": "https://sinacloud.net/vue-wechat/images/album/baiqian/baiqian02.jpeg",
                                    "date": 182625262
                                }
                            ],
                            "area": [
                                "九重天",
                                "洗梧宫"
                            ],
                            "from": "通过扫一扫",
                            "tag": "太子",
                            "desc": {
                                "title": "",
                                "picUrl": ""
                            }
                        }
                    ],
                    "Z": [
                        {
                            "wxid": "wxid_zhaohd",
                            "initial": "z",
                            "headerUrl": "https://sinacloud.net/vue-wechat/images/headers/header01.png",
                            "nickname": "阿荡",
                            "sex": 1,
                            "remark": "阿荡",
                            "signature": "填坑小能手",
                            "telphone": 18896586152,
                            "album": [
                                {
                                    "imgSrc": ""
                                }
                            ],
                            "area": [
                                "中国",
                                "北京",
                                "海淀"
                            ],
                            "from": "",
                            "tag": "",
                            "desc": {}
                        },
                        {
                            "wxid": "wxid_zhugeliang",
                            "initial": "z",
                            "headerUrl": "https://sinacloud.net/vue-wechat/images/headers/zhugeliang.jpg",
                            "nickname": "诸葛亮",
                            "sex": 1,
                            "remark": "诸葛亮",
                            "signature": "你可识得此阵？",
                            "telphone": 18896586152,
                            "album": [
                                {
                                    "imgSrc": "https://sinacloud.net/vue-wechat/images/album/baiqian/baiqian01.jpeg",
                                    "date": 182625262
                                },
                                {
                                    "imgSrc": "https://sinacloud.net/vue-wechat/images/album/guanyu/guanyu01.jpeg",
                                    "date": 182625262
                                }
                            ],
                            "area": [
                                "蜀国",
                                "荆州"
                            ],
                            "from": "通过扫一扫",
                            "tag": "卧龙",
                            "desc": {
                                "title": "",
                                "picUrl": ""
                            }
                        },
                        {
                            "wxid": "wxid_zhenji",
                            "initial": "z",
                            "headerUrl": "https://sinacloud.net/vue-wechat/images/headers/zhenji.jpg",
                            "nickname": "甄姬",
                            "sex": 0,
                            "remark": "甄姬",
                            "signature": "仿佛兮若轻云之蔽月",
                            "telphone": 18896586152,
                            "album": [
                                {
                                    "imgSrc": "https://sinacloud.net/vue-wechat/images/album/guanyu/guanyu01.jpeg",
                                    "date": 182625262
                                }
                            ],
                            "area": [
                                "魏",
                                "荆州",
                                "中山"
                            ],
                            "from": "通过手机号码添加",
                            "tag": "蜀",
                            "desc": {
                                "title": "",
                                "picUrl": ""
                            }
                        }
                    ]
                }
                return waiterLIst;
            }
        },
        mounted() {

        },
        methods: {
            toPs(i){
                window.scrollTo(0,this.$refs['key_'+i][0].offsetTop)
            }
        }
    }
</script>
<style>
    @import "../../assets/css/contact.css";
</style>
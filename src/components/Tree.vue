<template>
    <commonfiltertree :placeholder="placeholder"
        :data="data"
        :showCheckbox="showCheckbox"
        @check='getcheckdata'
        :showScreen="showScreen"
        @click='getCurrentKey'
        @checkkey='getCheckedKeys'
        :defaultExpandAll="defaultExpandAll"
        :default='defaults'></commonfiltertree>
</template>
<script>
import commonfiltertree from "@/components/filtertree.vue";
export default {
    components: {
        commonfiltertree
    },
    data() {
        return {
            placeholder: '输入信息，按回车搜索',
            showCheckbox: true,
            data: [{
                id: 1,
                label: '一级 1',
                children: [{
                    id: 4,
                    label: '二级 1-1',
                    children: [{
                        id: 9,
                        label: '三级 1-1-1'
                    }, {
                        id: 10,
                        label: '三级 1-1-2'
                    }]
                }]
            }, {
                id: 2,
                label: '一级 2',
                children: [{
                    id: 5,
                    label: '二级 2-1'
                }, {
                    id: 6,
                    label: '二级 2-2'
                }]
            }, {
                id: 3,
                label: '一级 3',
                children: [{
                    id: 7,
                    label: '二级 3-1'
                }, {
                    id: 8,
                    label: '二级 3-2'
                }]
            }],
            countent: "",
            defaultProps: {
                children: "children",
                label: "label"
            },
            data1: new Array,
            data2: "",
            showScreen: true,
            defaults: [],
            defaultExpandAll:true
            
        };
    },
    methods: {
        getcheckdata(data) {
            //有多选框的时候返回的data数组
            this.data1 = data;
        },
        getCurrentKey(data) {
            //点击的时候返回当前点击的key
            this.data2 = data;
        },
        getCheckedKeys(data) {
            //有多选框时返回的key所组成的数组
            this.data3 = data;
        }
    }
};
</script>
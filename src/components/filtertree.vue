/*
* @property { data :  {Array} 接口传来的数组 }
* @property { showCheckbox :  {Boolean} 是否显示多选小方框 }
* @property { placeholder :  {String} 提示语，上方搜索框提示语。 }
* @property { check : 父组件使用check来接收已选中的所有数据组成的数组 }
* @property { title : {String} 弹窗上方的名字 }
* @property { showScreen : {Boolean} 是否需要筛选框 }
* @property { nodeclick : 节点被点击时的回调 }
* @property { defaults : {Array} 默认选中的数据 传key组成的数组 }
* @property { defaultExpandAll : {Boolean} 是否默认展开 }
* @version 1.0.0
* @edit: 2018/8/2
*/
<template>
    <div class="air-tree-wrappers">
            <div class="el-dialog__title">{{ this.title }}</div>
        <div v-if="screen">
            <el-input class="input"
                :placeholder="placeholder"
                prefix-icon="el-icon-search"
                v-model="filterText"
            >
            </el-input>
        </div>
        <el-tree class="filter-tree"
            :data="data"
            :props="defaultProps"
            :show-checkbox="checkbox"
            :default-expand-all="defaultExpandAll"
            :filter-node-method="filterNode"
            @check-change='check()'
            ref="tree"
            :node-key="'id'"
            @node-click="nodeclick">
        </el-tree>
        <div class="foot">
        </div>
    </div>
</template>
<script>
export default {
    props: {
        placeholder: {
            type: String
        },
        data: {
            type: Array
        },
        default: {
            type: Array
        },
        showCheckbox: {
            type: Boolean
        },
        width: {
            type: String
        },
        title: {
            type: String
        },
        showScreen: {
            type: Boolean
        },
        defaultExpandAll: {
            type: Boolean,
        }
    },
    data() {
        return {
            filterText: '',
            countent: "",
            checkbox: this.showCheckbox,
            defaultProps: {
                children: "children",
                label: "label",
            },
            data1: new Array,
            dialogTableVisible: false,
            screen: this.showScreen
        };
    },
    watch: {
        filterText(val) {
            this.$refs.tree.filter(val);
        }
    },
    methods: {
        filterNode(value, data) {
            if (!value) return true;
            return data.label.indexOf(value) !== -1;
        },
        //传回父组件
        check() {
            //获取所有被选中的data的数组
            let takeDate = this.$refs.tree.getCheckedNodes();
            this.$emit('check', takeDate);
            //获取所有被选中的key的数组
            let keyDate = this.$refs.tree.getCheckedKeys();
            this.$emit('checkkey', keyDate);
        },
        nodeclick() {
            let key = this.$refs.tree.getCurrentKey()
            this.$emit('click', key);
        }
    }
};
</script>
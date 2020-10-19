<template>
    <div class="collapse-area">
        <div :class="isShowCollapseArea? 'showEdit': ''" class="add_category_row">
            <div class="add-form">
                <el-form label-width="120px">
                    <el-form-item v-for="(item,index) of fields" :key="index" :label="item.title">
                        <el-input v-model="form[item.value]" />
                    </el-form-item>
                    <el-form-item>
                        <el-button type="primary" @click="submit">提交</el-button>
                    </el-form-item>
                </el-form>
            </div>

        </div>
        <div class="add_button" @click="add">
            <i v-if="isShowCollapseArea" class="el-icon-caret-top edit_icon" />
            <i v-else slot="icon" class="el-icon-caret-bottom edit_icon" />
            <span>添加</span>
        </div>

    </div>
</template>

<script>
  export default {
    name: 'CollapseArea',
    props: {
      form: {
        type: Object,
        default() {
          return {}
        }
      },
      fields: {
        type: Array,
        default() {
          return []
        }
      }
    },
    data() {
      return {
        isShowCollapseArea: false
      }
    },
    methods: {
      submit() {
        this.$emit('submit', this.form)
      },
      add() {
        this.isShowCollapseArea = !this.isShowCollapseArea
      }
    }

  }
</script>
<style lang="scss" scoped>
    .collapse-area{
        .add_category_row{
            height: 0;
            overflow: hidden;
            transition: all 400ms;
            background: #f9fafc;
        }
        .add-form{
            background: #f9fafc;
            border: 1px solid #eaeefb;
            border-top: none;
        }
        .showEdit{
            height: 163px;
        }
        .add_button{
            text-align: center;
            line-height: 40px;
            border-bottom-right-radius: 6px;
            border-bottom-left-radius: 6px;
            border: 1px solid #eaeefb;
            border-top: none;
            transition: all 400ms;
            &:hover{
                background: #f9fafc;
                .edit_icon{
                    color: #20a0ff;
                }
            }
            .edit_icon{
                color: #ccc;
                transition: all 400ms;
            }
        }
    }

</style>

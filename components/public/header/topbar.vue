<template>
    <el-row :gutter="20">
        <el-col :span="6">
            <geo/>
        </el-col>
        <el-col 
        class="right"
        :span="6"><user /></el-col>
    </el-row>
</template>

<script>
import Geo from './geo'
import User from './user'
export default {
    components:{
        Geo,
        User
    }
}
</script>
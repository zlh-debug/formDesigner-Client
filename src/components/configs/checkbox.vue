<template>
	<div>
		<el-form size="small" :model="itemConf" label-width="100px" style="margin-right: 10%">
			<el-form-item label="ID">
				<el-input v-model="itemConf.id" disabled></el-input>
			</el-form-item>
			<el-form-item label="标签">
				<el-input v-model="itemConf.title"></el-input>
			</el-form-item>
			<el-form-item label="显示标签">
				<el-switch v-model="itemConf.showLabel"></el-switch>
			</el-form-item>
			<el-form-item label="是否必填">
				<el-switch v-model="itemConf.required"></el-switch>
			</el-form-item>
			<el-form-item label="是否禁用">
				<el-switch v-model="itemConf.disabled"></el-switch>
			</el-form-item>
			<el-form-item label="边框">
				<el-switch v-model="itemConf.childAttr.border"></el-switch>
			</el-form-item>
			<el-form-item v-show="itemConf.childIndex===1||itemConf.childAttr.border" label="尺寸">
				<el-select v-model="itemConf.size">
					<el-option label="中" value="medium"></el-option>
					<el-option label="小" value="small"></el-option>
					<el-option label="迷你" value="mini"></el-option>
				</el-select>
			</el-form-item>
			<el-form-item label="最小选择">
				<el-input-number v-model="itemConf.min" :min="0"></el-input-number>
			</el-form-item>
			<el-form-item label="最大选择">
				<el-input-number v-model="itemConf.max" :min="0"></el-input-number>
			</el-form-item>
			<el-form-item label="类型">
				<el-radio-group v-model="itemConf.childIndex">
					<el-radio-button :label="0">默认</el-radio-button>
					<el-radio-button :label="1">按钮</el-radio-button>
				</el-radio-group>
			</el-form-item>
			<el-form-item v-show="itemConf.childIndex===1" label="文本颜色">
				<el-color-picker v-model="itemConf['text-color']"></el-color-picker>
			</el-form-item>
			<el-form-item v-show="itemConf.childIndex===1" label="填充色">
				<el-color-picker v-model="itemConf.fill"></el-color-picker>
			</el-form-item>
		</el-form>
		<el-divider>选项</el-divider>
		<div v-for="(item, index) in itemConf.child" :key="index" style="overflow: hidden;margin-left: 10px;">
			<div style="float: left;margin-top: 5px;">
				<i class="el-icon-s-operation" />
			</div>
			<el-input v-model="item.label" placeholder="选项名" size="small"
				style="float: left;width: 80%;margin-left: 4%;margin-right:4%;margin-bottom:5px" />
			<div style="float: left;margin-top: 5px;" @click="itemConf.child.splice(index, 1)">
				<i class="el-icon-remove-outline" />
			</div>
		</div>
		<div style="margin-left: 20px;">
			<el-button style="padding-bottom: 0" icon="el-icon-circle-plus-outline" type="text" @click="addSelectItem">
				添加选项
			</el-button>
		</div>
	</div>
</template>

<script>
	export default {
		name: 'checkboxConf',
		props: {
			itemConf: {
				type: Object,
				default: () => ({})
			}
		},
		methods: {
			addSelectItem() {
				this.itemConf.child.push({
					label: ''
				})
			}
		}
	}
</script>

<style>
</style>

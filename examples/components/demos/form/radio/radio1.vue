/**
 *  author: eric
 *  create at: 2020-01-13 16:04:37
 */
<template>
	<div class="demo">
		值:{{yoRadio}}
		<p>{{langKey('单独使用')}}</p>
		<yo-radio v-model="single">{{langKey('单独使用')}}</yo-radio>
		<yo-radio v-model="single1" true-value="1" false-value="0">{{langKey('单独使用')}}</yo-radio>
		
		<p>{{langKey('默认样式&样式0')}}</p>
		<yo-radio v-model="yoRadio" :label="langKey('禁用')"></yo-radio>
		<yo-radio type="0" v-model="yoRadio" :label="langKey('选中且禁用')"></yo-radio>
		<p>{{langKey('样式1')}}</p>
		<yo-radio type="1" v-model="yoRadio" :label="langKey('禁用')"></yo-radio>
		<yo-radio type="1" v-model="yoRadio" :label="langKey('选中且禁用')"></yo-radio>
		<p>{{langKey('样式2')}}</p>
		<yo-radio type="2" v-model="yoRadio" :label="langKey('禁用')"></yo-radio>
		<yo-radio type="2" v-model="yoRadio" :label="langKey('选中且禁用')"></yo-radio>
		<p>{{langKey('样式3')}}</p>
		<yo-radio type="3" v-model="yoRadio" :label="langKey('禁用')"></yo-radio>
		<yo-radio type="3" v-model="yoRadio" :label="langKey('选中且禁用')"></yo-radio>

		<p>{{langKey('设置属性 border 可以显示边框。')}}</p>
		<yo-radio type="3" v-model="yoRadio" :label="langKey('禁用')"></yo-radio>
		<yo-radio border v-model="yoRadio" :label="langKey('选中且禁用')"></yo-radio>
		<yo-radio border round v-model="yoRadio" :label="langKey('选中且禁用')"></yo-radio>
		<yo-radio border circle v-model="yoRadio" :label="langKey('选中且禁用')"></yo-radio>
		<p>{{langKey('通过设置disabled属性来禁用单选框。')}}</p>
		<yo-radio v-model="yoRadio" disabled :label="langKey('禁用')"></yo-radio>
	</div>
</template>
<script>
export default {
	data() {
		return {
			yoRadio:'选中且禁用',
			single:false,
			single1:0,
		}
	},
	mounted() {
		this.$emit('loaded')
	},
}
</script>
<style lang="less" scoped>
	.demo{
		.yo-radio{
			margin-right: 10px;
		}
	}
</style>

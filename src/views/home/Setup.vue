<template>
	<el-dialog :title="setUp.setting" :visible.sync="visible" :append-to-body="true">
		<el-row :gutter="20">
			<el-col :span="7" :offset="2">
				{{setUp.languageSettings}}
			</el-col>
			<el-col :span="4">
				<el-radio v-model="language" label="jp">{{setUp.jp}}</el-radio>
			</el-col>
			<el-col :span="4">
				<el-radio v-model="language" label="en">{{setUp.en}}</el-radio>
			</el-col>
		</el-row>
	</el-dialog>
</template>

<script>
	import {
		mapState,
		mapActions
	} from 'vuex'
	export default {
		name: 'setUp',
		data() {
			return {
				visible: false,
				language: 'jp'
			}
		},
		computed: {
			...mapState('common', {
				lang: 'language'
			}),
			setUp() {
				return {
					setting: this.$t("language.setting"),
					languageSettings: this.$t("language.languageSettings"),
					jp: this.$t("language.jp"),
					en: this.$t("language.en")
				}
			}
		},
		methods: {
			...mapActions('common', ['updateLanguage']),
			// 初始化
			init() {
				this.visible = true
				this.language = this.lang
				this.$i18n.locale = this.lang
			}
		},
		watch: {
			language(val) {
				this.updateLanguage(val)
				this.$i18n.locale = this.lang
			}
		}
	}
</script>

<style>
</style>

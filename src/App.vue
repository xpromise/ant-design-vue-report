<template>
	<Card>
		<Form :label-col="{ span: 4 }">
			<FormItem v-bind="validateInfos.name" label="name">
				<Input v-model:value="formState.name" />
			</FormItem>
			<FormItem v-bind="validateInfos.desc" label="desc">
				<Textarea v-model:value="formState.desc" />
			</FormItem>
			<FormItem>
				<Button type="primary" @click.prevent="submit">确定</Button>
				<Button>取消</Button>
			</FormItem>
		</Form>
	</Card>
</template>

<script setup>
import { reactive } from "vue";
import { Card, Form, FormItem, Input, Textarea, Button } from "ant-design-vue";

const formState = reactive({
	name: "",
	desc: "",
});
const rules = reactive({
	name: [{ required: true, message: "请输入名称", trigger: "blur" }],
	desc: [{ required: true, message: "请输入描述", trigger: "blur" }],
});

const { validateInfos, validate } = Form.useForm(formState, rules);

const submit = async () => {
	await validate();
};
</script>

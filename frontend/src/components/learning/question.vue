<template>
    <div class="panel panel-default">
        <strong>{{ question.title }} </strong><span v-if="exercise.answered" class="badge badge-success">Done</span>
        <br>
        {{ question.task }}
        <br>
        <br>
        <b-row>
            <div class="editor_form">
                <editor v-model="question.answer" @init="editorInit" lang="python" theme="chrome" width="100%"
                        height="100%"> </editor>
                <div class="form-actions">
                    <b-button type="submit" variant="success" @click.prevent="answer()" v-if="!question.answered">
                        Submit
                    </b-button>
                    <b-button variant="warning" @click.prevent="new_answer()" v-if="question.answered">Update
                    </b-button>
                </div>
            </div>
        </b-row>
    </div>
</template>

<script>
    import axios from 'axios';
    import 'prismjs/themes/prism.css'

    export default {
        name: "question",
        props: {
            question: {
                type: Object,
                required: true
            }
        },
        components: {
            editor: require('vue2-ace-editor')
        },
        methods: {
            answer() {
                let data = {
                    "answer": this.exercise.answer,
                    "exercise": this.exercise.id,
                    "status": "Done"
                };
                axios.post('/exercise/', data).then((resp) => {
                    this.exercise.answered = true
                    this.exercise.status = "Done"
                    this.$swal('Done', "Answer saved", "success")
                })
            },
            new_answer() {
                let data = {
                    "answer": this.exercise.answer,
                    "exercise": this.exercise.id
                };
                axios.put('/exercise/', data).then(
                    this.$swal('Done', "Answer updated", "success")
                )
            },
            editorInit() {
                require('brace/ext/language_tools');
                require('brace/mode/python');
                // require('brace/theme/dracula'); TODO: add ability to change themes
                require('brace/theme/chrome');
            }
        },
        created() {
            let self = this;
            if (!('answer' in self.question)) {
                self.question['answer'] = '';
                return self
            }
        }
    }
</script>

<style scoped>
    .editor_form {
        min-height: 400px;
        min-width: 100%;
    }
</style>
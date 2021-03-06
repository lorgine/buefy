<template>
    <div class="container">
        <h1 class="title is-spaced">Dialog</h1>
        <h2 class="subtitle">Dialogs inform users about a specific task and may contain critical information or require decisions</h2>
        <hr>

        <h3 class="title">Alert</h3>
        <div class="block">
            <button class="button is-medium is-primary" @click="alert">
                Alert (default)
            </button>
            <button class="button is-medium is-primary" @click="alertCustom">
                Alert (custom)
            </button>
        </div>
        <pre v-highlight><code class="javascript">{{ code1 | pre }}</code></pre>

        <hr>

        <h3 class="title">Confirm</h3>
        <div class="block">
            <button class="button is-medium is-info" @click="confirm">
                Confirm (default)
            </button>

            <button class="button is-medium is-info" @click="confirmCustom">
                Confirm (custom)
            </button>

            <button class="button is-medium is-danger" @click="confirmCustomDelete">
                Confirm (custom)
            </button>
        </div>
        <pre v-highlight><code class="javascript">{{ code2 | pre }}</code></pre>

        <hr>

        <h3 class="title">Prompt</h3>
        <div class="block">
            <button class="button is-medium is-dark" @click="prompt">
                Prompt
            </button>
        </div>
        <pre v-highlight><code class="javascript">{{ code3 | pre }}</code></pre>

        <hr>

        <h2 class="title is-spaced">API</h2>
        <b-tabs>
            <b-tab-item label="Properties">
                <b-table :data="props" default-sort="name">
                    <template scope="props">
                        <b-table-column field="name" label="Name">
                            <span v-html="props.row.name"></span>
                        </b-table-column>
                        <b-table-column field="description" label="Description" width="620">
                            <span v-html="props.row.description"></span>
                        </b-table-column>
                        <b-table-column field="type" label="Type">
                            <span v-html="props.row.type"></span>
                        </b-table-column>
                        <b-table-column field="values" label="Values">
                            <span v-html="props.row.values"></span>
                        </b-table-column>
                        <b-table-column field="default" label="Default">
                            <span v-html="props.row.default"></span>
                        </b-table-column>
                    </template>
                </b-table>
            </b-tab-item>
        </b-tabs>
    </div>
</template>

<script>
    export default {
        data() {
            return {
                props: [
                    {
                        name: '<code>type</code>',
                        description: 'Type (color) of the confirm button (and the icon if <code>hasIcon</code>)',
                        type: 'String',
                        values: `<code>is-white</code>, <code>is-black</code>, <code>is-light</code>,
                            <code>is-dark</code>, <code>is-primary</code>, <code>is-info</code>, <code>is-success</code>,
                            <code>is-warning</code>, <code>is-danger</code>,
                            and any other colors you've set in the <code>$colors</code> list on Sass`,
                        default: '<code>is-primary</code>'
                    },
                    {
                        name: '<code>title</code>',
                        description: 'Dialog title',
                        type: 'String',
                        values: '—',
                        default: '—'
                    },
                    {
                        name: '<code>message</code>',
                        description: 'Message text',
                        type: 'String',
                        values: '—',
                        default: '—'
                    },
                    {
                        name: '<code>hasIcon</code>',
                        description: 'Adds an icon on the left side depending on the <code>type</code>',
                        type: 'Boolean',
                        values: '—',
                        default: '<code>false</code>'
                    },
                    {
                        name: '<code>confirmText</code>',
                        description: 'Text of the confirm button',
                        type: 'String',
                        values: '—',
                        default: '<code>OK</code>'
                    },
                    {
                        name: '<code>cancelText</code>',
                        description: 'Text of the cancel button',
                        type: 'String',
                        values: '—',
                        default: '<code>Cancel</code>'
                    },
                    {
                        name: '<code>canCancel</code>',
                        description: 'If the dialog can be canceled',
                        type: 'String',
                        values: '—',
                        default: '<code>true</code> for Confirm/Prompt, <code>false</code> for Alert'
                    },
                    {
                        name: '<code>inputPlaceholder</code>',
                        description: `Prompt only: input's placeholder`,
                        type: 'String',
                        values: '—',
                        default: '—'
                    },
                    {
                        name: '<code>inputName</code>',
                        description: `Prompt only: input's native name`,
                        type: 'String',
                        values: '—',
                        default: '—'
                    },
                    {
                        name: '<code>inputMaxlength</code>',
                        description: `Prompt only: input's maxlength`,
                        type: 'Number',
                        values: '—',
                        default: '—'
                    },
                    {
                        name: '<code>onConfirm</code>',
                        description: 'Callback function when the confirm button is clicked',
                        type: 'Function (value: String)',
                        values: '—',
                        default: '—'
                    },
                    {
                        name: '<code>onCancel</code>',
                        description: 'Callback function when the dialog is canceled (cancel button is clicked / pressed escape / clicked outside)',
                        type: 'Function',
                        values: '—',
                        default: '—'
                    }
                ],
                code1: `
                export default {
                    methods: {
                        alert() {
                            this.$dialog.alert('Everything looks fine!')
                        },
                        alertCustom() {
                            this.$dialog.alert({
                                title: 'Title Alert',
                                message: 'I have a title, a custom button and <b>HTML</b>!',
                                confirmText: 'Cool!'
                            })
                        }
                    }
                }`,
                code2: `
                export default {
                    methods: {
                        confirm() {
                            this.$dialog.confirm({
                                message: 'Continue on this task?',
                                onConfirm: () => {
                                    this.$toast.open('User confirmed')
                                }
                            })
                        },
                        confirmCustom() {
                            this.$dialog.confirm({
                                title: 'Privacy Politics',
                                message: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit. [...]',
                                cancelText: 'Disagree',
                                confirmText: 'Agree',
                                type: 'is-success',
                                onConfirm: () => {
                                    this.$toast.open('User agreed')
                                }
                            })
                        },
                        confirmCustomDelete() {
                            this.$dialog.confirm({
                                title: 'Deleting account',
                                message: 'Are you sure you want to <strong>delete</strong> your account? This action cannot be undone.',
                                confirmText: 'Delete Account',
                                type: 'is-danger',
                                hasIcon: true,
                                onConfirm: () => {
                                    this.$toast.open('Account deleted!')
                                }
                            })
                        }
                    }
                }`,
                code3: `
                export default {
                    methods: {
                        prompt() {
                            this.$dialog.prompt({
                                message: \`What's your name?\`,
                                maxlength: 20,
                                placeholder: 'e.g. John Doe',
                                onConfirm: (value) => {
                                    this.$toast.open('Your name is: ' + value)
                                }
                            })
                        }
                    }
                }`
            }
        },
        methods: {
            alert() {
                this.$dialog.alert('Everything looks fine!')
            },
            alertCustom() {
                this.$dialog.alert({
                    title: 'Title Alert',
                    message: 'I have a title, a custom button and <b>HTML</b>!',
                    confirmText: 'Cool!'
                })
            },
            confirm() {
                this.$dialog.confirm({
                    message: 'Continue on this task?',
                    onConfirm: () => {
                        this.$toast.open('User confirmed')
                    }
                })
            },
            confirmCustom() {
                this.$dialog.confirm({
                    title: 'Privacy Politics',
                    message: `Lorem ipsum dolor sit amet, consectetur adipiscing elit. Fusce id fermentum quam. Proin sagittis,
                        nibh id hendrerit imperdiet, elit sapien laoreet elit, ac scelerisque diam velit in nisl. Nunc maximus ex non
                        laoreet semper. Nunc scelerisque, libero sit amet pretium dignissim, augue purus placerat justo,
                        sit amet porttitor dui metus in nisl. Nulla non leo placerat, porta metus eu, laoreet risus.
                        Etiam lacinia, purus eu luctus maximus, elit ex viverra tellus, sit amet sodales quam dui nec odio.
                        Nullam porta mollis est. Quisque aliquet malesuada fringilla. Pellentesque volutpat lacus at ante posuere,
                        non pulvinar ante porta. Proin viverra eu massa nec porta. Aliquam rhoncus velit quis sem hendrerit,
                        ut dictum nisl accumsan. Maecenas erat enim, scelerisque non ligula ac, eleifend venenatis ligula.
                        Praesent molestie mauris sed elit posuere, non malesuada libero gravida. In hac habitasse platea dictumst.
                        Pellentesque habitant morbi tristique senectus et netus et malesuada fames ac turpis egestas.`,
                    cancelText: 'Disagree',
                    confirmText: 'Agree',
                    type: 'is-success',
                    onConfirm: () => {
                        this.$toast.open('User agreed')
                    }
                })
            },
            confirmCustomDelete() {
                this.$dialog.confirm({
                    title: 'Deleting account',
                    message: 'Are you sure you want to <b>delete</b> your account? This action cannot be undone.',
                    confirmText: 'Delete Account',
                    type: 'is-danger',
                    hasIcon: true,
                    onConfirm: () => {
                        this.$toast.open('Account deleted!')
                    }
                })
            },
            prompt() {
                this.$dialog.prompt({
                    message: `What's your name?`,
                    inputMaxlength: 20,
                    inputPlaceholder: 'e.g. John Doe',
                    onConfirm: (value) => {
                        this.$toast.open('Your name is: ' + value)
                    }
                })
            }
        }
    }
</script>

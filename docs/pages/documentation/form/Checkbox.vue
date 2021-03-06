<template>
    <div class="container">
        <h1 class="title is-spaced">Checkbox</h1>
        <h2 class="subtitle">Select a single or grouped options</h2>
        <hr>

        <div class="columns">
            <div class="column">
                <div class="block">
                    <b-checkbox>Basic</b-checkbox>
                    <b-checkbox v-model="checkbox">{{ checkbox }}</b-checkbox>
                    <b-checkbox disabled>Disabled</b-checkbox>
                    <b-checkbox disabled checked>Disabled Checked</b-checkbox>
                </div>

                <h3 class="subtitle">Vertical example</h3>
                <div class="field">
                    <b-checkbox>Basic</b-checkbox>
                </div>

                <div class="field">
                    <b-checkbox v-model="checkbox">{{ checkbox }}</b-checkbox>
                </div>

                <div class="field">
                    <b-checkbox disabled>Disabled</b-checkbox>
                </div>

                <div class="field">
                    <b-checkbox disabled checked>Disabled Checked</b-checkbox>
                </div>
            </div>
            <div class="column">
                <pre class="content" v-highlight><code class="html">{{ template1 | pre }}</code></pre>
                <pre v-highlight><code class="javascript">{{ code1 | pre }}</code></pre>
            </div>
        </div>

        <hr>
        <h2 class="title">Checkbox Group</h2>
        <div class="columns">
            <div class="column">
                <div class="block">
                    <b-checkbox-group v-model="checkboxGroup">
                        <b-checkbox custom-value="Silver">Silver</b-checkbox>
                        <b-checkbox custom-value="Flint">Flint</b-checkbox>
                        <b-checkbox custom-value="Vane">Vane</b-checkbox>
                        <b-checkbox custom-value="Billy" disabled>Billy</b-checkbox>
                    </b-checkbox-group>
                </div>
                <p class="content"><b>Selection:</b> {{ checkboxGroup }}</p>

                <h3 class="subtitle">Vertical example</h3>
                <b-checkbox-group v-model="checkboxGroup">
                    <div class="field">
                        <b-checkbox custom-value="Silver">Silver</b-checkbox>
                    </div>

                    <div class="field">
                        <b-checkbox custom-value="Flint">Flint</b-checkbox>
                    </div>

                    <div class="field">
                        <b-checkbox custom-value="Vane">Vane</b-checkbox>
                    </div>

                    <div class="field">
                        <b-checkbox custom-value="Billy" disabled>Billy</b-checkbox>
                    </div>
                </b-checkbox-group>
            </div>
            <div class="column">
                <pre class="content" v-highlight><code class="html">{{ template2 | pre }}</code></pre>
                <pre v-highlight><code class="javascript">{{ code2 | pre }}</code></pre>
            </div>
        </div>

        <hr>

        <h2 class="title is-spaced">API</h2>
        <h3 class="subtitle">Checkbox</h3>
        <b-tabs>
            <b-tab-item label="Properties">
                <b-table :data="checkboxProps" default-sort="name">
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

            <b-tab-item label="Events">
                <b-table :data="checkboxEvents" default-sort="name">
                    <template scope="props">
                        <b-table-column field="name" label="Name">
                            <span v-html="props.row.name"></span>
                        </b-table-column>
                        <b-table-column field="description" label="Description" width="620">
                            <span v-html="props.row.description"></span>
                        </b-table-column>
                        <b-table-column field="parameters" label="Parameters">
                            <span v-html="props.row.parameters"></span>
                        </b-table-column>
                    </template>
                </b-table>
            </b-tab-item>
        </b-tabs>

        <h3 class="subtitle">Checkbox Group</h3>
        <b-tabs>
            <b-tab-item label="Properties">
                <b-table :data="checkboxGroupProps" default-sort="name">
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

            <b-tab-item label="Events">
                <b-table :data="checkboxGroupEvents" default-sort="name">
                    <template scope="props">
                        <b-table-column field="name" label="Name">
                            <span v-html="props.row.name"></span>
                        </b-table-column>
                        <b-table-column field="description" label="Description" width="620">
                            <span v-html="props.row.description"></span>
                        </b-table-column>
                        <b-table-column field="parameters" label="Parameters">
                            <span v-html="props.row.parameters"></span>
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
                checkbox: true,
                checkboxGroup: ['Flint'],
                checkboxProps: [
                    {
                        name: '<code>v-model</code>',
                        description: 'Binding value',
                        type: 'Boolean',
                        values: '—',
                        default: '<code>false</code>'
                    },
                    {
                        name: '<code>custom-value</code>',
                        description: 'Native value when used inside a Checkbox Group',
                        type: 'String, Number, Boolean',
                        values: '—',
                        default: '—'
                    },
                    {
                        name: '<code>disabled</code>',
                        description: 'Same as native <code>disabled</code>',
                        type: 'Boolean',
                        values: '—',
                        default: '<code>false</code>'
                    },
                    {
                        name: '<code>name</code>',
                        description: 'Same as native <code>name</code>',
                        type: 'String',
                        values: '—',
                        default: '—'
                    },
                    {
                        name: '<code>checked</code>',
                        description: 'Same as native <code>checked</code>',
                        type: 'Boolean',
                        values: '—',
                        default: '<code>false</code>'
                    }
                ],
                checkboxEvents: [
                    {
                        name: '<code>change</code>',
                        description: 'Triggers when the value of checkbox changes',
                        parameters: '<code>value: Boolean</code>, <code>event: $event</code>'
                    }
                ],
                checkboxGroupProps: [
                    {
                        name: '<code>v-model</code>',
                        description: 'Binding value',
                        type: 'Array',
                        values: '—',
                        default: '—'
                    }
                ],
                checkboxGroupEvents: [
                    {
                        name: '<code>change</code>',
                        description: 'Triggers when the value of any checkbox changes',
                        parameters: '<code>value: Array</code></code>'
                    }
                ],
                template1: `
                <div class="block">
                    <b-checkbox>Basic</b-checkbox>
                    <b-checkbox v-model="checkbox">{{ checkbox }}</b-checkbox>
                    <b-checkbox disabled>Disabled</b-checkbox>
                    <b-checkbox disabled checked>Disabled Checked</b-checkbox>
                </div>

                <h3 class="subtitle">Vertical</h3>
                <div class="field">
                    <b-checkbox>Basic</b-checkbox>
                </div>
                <div class="field">
                    <b-checkbox v-model="checkbox">{{ checkbox }}</b-checkbox>
                </div>
                <div class="field">
                    <b-checkbox disabled>Disabled</b-checkbox>
                </div>
                <div class="field">
                    <b-checkbox disabled checked>Disabled Checked</b-checkbox>
                </div>`,
                code1: `
                export default {
                    data() {
                        return {
                            checkbox: true
                        }
                    }
                }`,
                template2: `
                <div class="block">
                    <b-checkbox-group v-model="checkboxGroup">
                        <b-checkbox custom-value="Silver">Silver</b-checkbox>
                        <b-checkbox custom-value="Flint">Flint</b-checkbox>
                        <b-checkbox custom-value="Vane">Vane</b-checkbox>
                        <b-checkbox custom-value="Billy" disabled>Billy</b-checkbox>
                    </b-checkbox-group>
                </div>
                <p class="content"><b>Selection:</b> {{ checkboxGroup }}</p>

                <h3 class="subtitle">Vertical example</h3>
                <b-checkbox-group v-model="checkboxGroup">
                    <div class="field">
                        <b-checkbox custom-value="Silver">Silver</b-checkbox>
                    </div>
                    <div class="field">
                        <b-checkbox custom-value="Flint">Flint</b-checkbox>
                    </div>
                    <div class="field">
                        <b-checkbox custom-value="Vane">Vane</b-checkbox>
                    </div>
                    <div class="field">
                        <b-checkbox custom-value="Billy" disabled>Billy</b-checkbox>
                    </div>
                </b-checkbox-group>`,
                code2: `
                export default {
                    data() {
                        return {
                            checkboxGroup: ['Flint']
                        }
                    }
                }`
            }
        }
    }
</script>

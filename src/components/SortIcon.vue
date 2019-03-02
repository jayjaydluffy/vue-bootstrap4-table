<template>
<span>
    <span class="ml-2" v-if="order == 'asc'">
        <template>
            <slot name="vbt-sort-asc-icon">

            </slot>
        </template>
    </span>   

    <span class="ml-2" v-else-if="order==='desc'">
        <template>
            <slot name="vbt-sort-desc-icon">

            </slot>
        </template>
    </span>

    <span class="ml-2" v-else-if="order !== 'asc' && order !== 'desc' && displaySortableIcon">
        <template>
            <slot name="vbt-no-sort-icon">

            </slot>
        </template>
    </span>
</span>
</template>

<script>
import findIndex from "lodash/findIndex";


export default {
    name: 'SortIcon',
    props: {
        sort: {
            type: Array,
            default: function () {
                return [];
            }
        },
        column: {
            type: Object,
            default: function () {
                return {};
            }
        },
        displaySortableIcon: {
            type: Boolean,
            default: true
        }
    },
    data: function () {
        return {

        }
    },
    mounted() {

    },
    methods: {

    },
    computed: {
        order() {
            let index = findIndex(this.sort, {
                'vbt_col_id': this.column.vbt_col_id
            });
            if (index == -1) {
                return null;
            } else {
                return this.sort[index].order;
                // if (this.sort[res].order) {

                // }
                // return this.sort[res].order == "asc" ? "desc" : "asc";
            }
        }
    },
}
</script>

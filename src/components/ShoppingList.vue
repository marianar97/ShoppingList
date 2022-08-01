<template>
    <div class="container">
        <h2>Shopping List</h2>
        <div>
            <input type="text" placeholder="Enter shopping item" class="form-control" v-on:keydown.enter="getItem" v-model="currentItem">
            <ul class="list-group mt-1">
                <li class="list-group-item shop-item" v-bind:class="{completed: item.completed}" v-for="item in list" v-bind:key="item.idItem">
                    <input class="form-check-input checkbox-item" type="checkbox" value="" id="flexCheckDefault" v-model="item.completed">
                    {{item.name}}
                </li>
            </ul>
        </div>
    </div>
</template>

<script>
    export default {
        name: 'ShoppingList',
        data() {
            return {
                idItem: 2,
                currentItem: '',
                list: [
                    {
                        id: 1,
                        name: 'banana',
                        completed: false
                    }
                ]
            }
        },
        methods: {
            getItem(){
                if (this.currentItem.trim().length == 0) {
                    return
                }
                this.list.push({
                    id: this.idItem,
                    name: this.currentItem,
                    completed: false 
                })
                this.currentItem = '';
                this.idItem++;
            }
        }
    }
</script>


<style scoped>

.shop-item {
    text-align: left;
}

.checkbox-item{
    margin-right: 10px;
}

.completed {
    text-decoration: line-through;
    color: gray;
}

</style>
<template>
  <div>
    <div class="center">
        <div v-if="list.length > 0" id="list-item">
            <draggable
                :list="list"
                v-bind="dragOptions"
            >
                <div v-for="(item, index) in list" :key="item.position" class="item">
                    <div class="zone-drag handle">
                        <button class="item--drag" @click="dragItem"> Drag </button>
                    </div>
                    <div class="zone-input">
                        <input type="text" :value="item.text" class="item--input">
                    </div>
                    <div class="zone-delete">
                        <button class="item--delete" @click="deleteItem(index)"> Delete </button>
                    </div>
                </div>

            </draggable>
        </div>
        <div v-else class="item item-nodata">
            <span>No Data</span>
        </div>
        <div>
            <button class="item--push" @click="addItem()"> + </button>
        </div>
    </div>
  </div>
</template>

<script>
import draggable from 'vuedraggable';

export default {
    name: 'DragDrop',
    components: {
        draggable,
    },
    computed: {
        dragOptions() {
            return {
                animation: 150,
                group: 'list',
                handle: ".handle",
                ghostClass: "ghost"
            };
        }
    },
    data() {
        return {
            list: [
                {
                    text: 'This is item 1',
                    position: 1
                },
                {
                    text: 'This is item 2',
                    position: 2
                },
                {
                    text: 'This is item 3',
                    position: 3
                },
                {
                    text: 'This is item 4',
                    position: 4
                }
            ]
        }
    },
    methods: {
        addItem() {
            var length = this.list.length;
            var i = 0;

            for (i; i < length; i++) {
                this.list[i].position = i + 1;
            }

            if (length === 0) {
                var newItem = {
                    text: '',
                    position: 1
                };

                this.list.push(newItem);
            } else {
                var newItems = {
                    text: '',
                    position: this.list.length + 1
                };

                this.list.push(newItems);
            }
        },

        deleteItem(position) {
            this.list.splice(position, 1);
        },

        dragItem() {
            const list = document.getElementById('list-item');

            console.log(list);
                
        }
    }
}
</script>

<style>
    .center {
        margin: 0 auto;
        width: 30%;
    }

    .item {
        width: 100%;
        min-height: 50px;
        background-color: #bce6eb;
        margin-top: 5px;
        margin-bottom: 5px;
        color: #ffffff;
        display: inline-flex;
        justify-content: center;
        align-items: center;
        border-radius: 3px;
    }

    .zone-drag {
        width: 20%;
        float: left;
        margin-left: 5px;
        margin-right: 5px;
    }

    .zone-input {
        width: 60%;
        float: left;
        margin-left: 5px;
        margin-right: 5px;
    }

    .zone-delete {
        width: 20%;
        float: left;
        margin-left: 5px;
        margin-right: 5px;
    }

    .item--input {
        width: 90%;
        height: 90%;
        overflow: hidden;
        padding-top: 10px;
        padding-bottom: 10px;
        padding-left: 5px;
        padding-right: 5px;
        border: none;
        border-radius: 5px;
    }

    .item--input:focus {
        outline: none;
    }

    .item--push {
        width: 35px;
        height: 35px;
        border: none;
        border-radius: 100%;
        background-color: #fdcfdf;
        cursor: pointer;
    }

    .item--push:focus {
        outline: none;
    }

    .item--drag {
        border: none;
        background-color: #fdcfdf;
        cursor: pointer;
        width: 80px;
        padding-top: 10px;
        padding-bottom: 10px;
        border-radius: 5px;
    }

    .item--drag:focus {
        outline: none;
    }

    .item--delete {
        border: none;
        background-color: #fdcfdf;
        cursor: pointer;
        width: 80px;
        padding-top: 10px;
        padding-bottom: 10px;
        border-radius: 5px;
    }

    .item--delete:focus {
        outline: none;
    }

    .item-nodata {
        width: 100%;
        height: 100%;
        overflow: hidden;
        display: flex;
        justify-content: center;
        align-items: center;
        color: #333;
    }

    .ghost {
        opacity: 0.5;
    }

</style>
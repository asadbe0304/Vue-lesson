<template>
        <li class="list-group-item d-flex justify-content-between"
                :class="[{ like: movie.like }, { favourite: movie.favourite }]">
                <span class="list-group-item-label" @click='onLike'> {{ movie.name }} </span>
                <input type="number" class="list-group-item-input" v-bind:value="movie.views" />
                <div class="d-flex justify-content-center align-items-center gap-2">
                        <button type="button" class="btn-cookie btn-sm rounded border-0 btn-dark">
                                <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" fill="currentColor"
                                        class="bi bi-database-fill-check" viewBox="0 0 16 16">
                                        <path
                                                d="M12.5 16a3.5 3.5 0 1 0 0-7 3.5 3.5 0 0 0 0 7Zm1.679-4.493-1.335 2.226a.75.75 0 0 1-1.174.144l-.774-.773a.5.5 0 0 1 .708-.708l.547.548 1.17-1.951a.5.5 0 1 1 .858.514ZM8 1c-1.573 0-3.022.289-4.096.777C2.875 2.245 2 2.993 2 4s.875 1.755 1.904 2.223C4.978 6.711 6.427 7 8 7s3.022-.289 4.096-.777C13.125 5.755 14 5.007 14 4s-.875-1.755-1.904-2.223C11.022 1.289 9.573 1 8 1Z" />
                                        <path
                                                d="M2 7v-.839c.457.432 1.004.751 1.49.972C4.722 7.693 6.318 8 8 8s3.278-.307 4.51-.867c.486-.22 1.033-.54 1.49-.972V7c0 .424-.155.802-.411 1.133a4.51 4.51 0 0 0-4.815 1.843A12.31 12.31 0 0 1 8 10c-1.573 0-3.022-.289-4.096-.777C2.875 8.755 2 8.007 2 7Zm6.257 3.998L8 11c-1.682 0-3.278-.307-4.51-.867-.486-.22-1.033-.54-1.49-.972V10c0 1.007.875 1.755 1.904 2.223C4.978 12.711 6.427 13 8 13h.027a4.552 4.552 0 0 1 .23-2.002Zm-.002 3L8 14c-1.682 0-3.278-.307-4.51-.867-.486-.22-1.033-.54-1.49-.972V13c0 1.007.875 1.755 1.904 2.223C4.978 15.711 6.427 16 8 16c.536 0 1.058-.034 1.555-.097a4.507 4.507 0 0 1-1.3-1.905Z" />
                                </svg>
                        </button>
                        <button type="button" class="btn-trash rounded border-0 btn-danger">
                                <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" fill="currentColor"
                                        class="bi bi-trash3" viewBox="0 0 16 16">
                                        <path
                                                d="M6.5 1h3a.5.5 0 0 1 .5.5v1H6v-1a.5.5 0 0 1 .5-.5ZM11 2.5v-1A1.5 1.5 0 0 0 9.5 0h-3A1.5 1.5 0 0 0 5 1.5v1H2.506a.58.58 0 0 0-.01 0H1.5a.5.5 0 0 0 0 1h.538l.853 10.66A2 2 0 0 0 4.885 16h6.23a2 2 0 0 0 1.994-1.84l.853-10.66h.538a.5.5 0 0 0 0-1h-.995a.59.59 0 0 0-.01 0H11Zm1.958 1-.846 10.58a1 1 0 0 1-.997.92h-6.23a1 1 0 0 1-.997-.92L3.042 3.5h9.916Zm-7.487 1a.5.5 0 0 1 .528.47l.5 8.5a.5.5 0 0 1-.998.06L5 5.03a.5.5 0 0 1 .47-.53Zm5.058 0a.5.5 0 0 1 .47.53l-.5 8.5a.5.5 0 1 1-.998-.06l.5-8.5a.5.5 0 0 1 .528-.47ZM8 4.5a.5.5 0 0 1 .5.5v8.5a.5.5 0 0 1-1 0V5a.5.5 0 0 1 .5-.5Z" />
                                </svg>
                        </button>
                        <i class="bi bi-star-fill"></i>
                </div>
        </li>
</template>
<script>
export default {
        props: {
                movie: {
                        type: Object,
                        required: true,
                }
        },
        methods: {
                onLike() {
                        this.$emit("onLike", this.movie.id)
                }
        },
};
</script>
<style scoped>
.list-group-item {
        padding: 15px 20px;
        border-bottom: 1px solid #3d5a80;
}

.list-group-item:last-child {
        border-bottom: none;
}

.list-group-item span {
        line-height: 35px;
        font-size: 20px;
        cursor: pointer;
        width: 550px;
}

.list-group-item input {
        line-height: 35px;
        font-size: 20px;
        text-align: center;
        border: 0;
        outline: none;
}

.list-group-item button {
        line-height: 35px;
        font-size: 17px;
        border: 0;
        margin: 3px;
        width: 35px;
        height: 35px;
}

.list-group-item button .btn-cookie {
        color: #e09 !important;
}

.list-group-item .bi-star-fill {
        opacity: 0;
        transform: translateX(10px);
        transition: all .5s cubic-bezier(0.165, 0.84, 0.44, 1);
}

.list-group-item.like .bi-star-fill {
        opacity: 1;
        transform: translateX(0px);
}

.list-group-item.favourite .list-group-item-label,
.list-group-item.favourite .list-group-item-label {
        color: #db9c12;
}
</style>

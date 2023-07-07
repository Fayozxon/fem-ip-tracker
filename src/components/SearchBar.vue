<script>
export default {
    data() {
        return {
            ipAddress: ''
        }
    },
    methods: {
        getData() {
            if (this.ipAddress.length) this.$emit('loadData', this.ipAddress);
            this.ipAddress = ''
        }
    }
}
</script>

<template>
  
    <div class="search-bar">
        <input
          v-model="ipAddress"
          @keypress.enter="getData"
          type="text"
          class="input"
          placeholder="Search for any IP address">
        <button @click="getData" type="submit" class="search-btn">
            <img src="../assets/icon-arrow.svg">
        </button>
    </div>

</template>

<style scoped>
.search-bar {
    max-width: 555px;
    margin: 0 auto;
    background: var(--clr-light);
    border-radius: 15px;
    overflow: hidden;
    display: flex;
    align-items: center;
    justify-content: space-between;
}

.search-bar .input {
    width: 100%;
    padding: 20px 25px;
    border: none;
    background: transparent;
    outline: none;
}

.search-bar .input::placeholder {
    color: var(--clr-grey);
}

.search-bar .search-btn {
    padding: 20px 25px;
    border: none;
    background: var(--clr-dark);
    cursor: pointer;
    transition: 200ms;
}

.search-bar .search-btn:hover {
    background: #3F3F3F;
}

/* RWD */
@media only screen and (max-width: 830px) {
    .search-bar {
        font-size: 1rem;
    }
}
</style>
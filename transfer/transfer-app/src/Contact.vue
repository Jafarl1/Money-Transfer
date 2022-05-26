<template>
    <li class="item">
        <div class="iteminfo">
            <p class="id">
              {{ contact.id }}
            </p>
            <span class="name">
              {{ contact.name }}
            </span>
        </div>    
        <span class="limit">
            {{ contact.limit > 0 ? 'You can send '+ contact.limit + ' AZN' : 'Limit exceeded!' }}
        </span>
        <button 
            class="btn" 
            :disabled="contact.limit === 0"
            v-on:click="$emit('search-contact', contact.id)"
        >
            Search
        </button>
    </li>
</template>

<script>
    export default {
      props: {
        contact: {
          type: Object,
          required: true,
        },
      },
    };
</script>

<style scoped>
    .item {
      width: 100%;
      height: 40px;
      display: flex;
      justify-content: space-between;
      align-items: center;
      padding: 0px 5px;
      border-radius: 4px;
    }
    .item:hover {
        background-color: rgb(238, 238, 238);
    }
    .item:hover .limit {
        visibility: visible;
    }
    .iteminfo {
      display: flex;
      font-size: 20px;
    }
    .id {
      width: 40px;
      display: flex;
      justify-content: end;
      padding-right: 15px;
    }
    .btn {
      height: 80%;
      border-radius: 3px;
      border: 2px solid darkblue;
      color: darkblue;
      background-color: gold;
      font-size: 16px;
      cursor: pointer;
      transition: 0.3s;
      padding: 0px 10px;
    }
    .btn:hover {
      transform: scale(1.05);
    }
    .btn:active {
      transform: scale(0.95);
    }
    .btn:disabled {
        border: 2px solid gray;
        color: gray;
    }
    .btn:disabled:hover{
        transform: scale(1);
    }
    .limit {
        width: 100%;
        text-align: end;
        padding-right: 25px;
        color: rgb(185, 185, 185);
        visibility: hidden;
    }

</style>
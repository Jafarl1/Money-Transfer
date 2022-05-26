<template>
  <div class="wallet">
    <h1 class="header">Wallet</h1>
    <h2 class="balance">Balance: {{ balance }} AZN</h2>
    <form 
        id="form"
        class="sendto"
        v-on:submit.prevent="onSubmit()"
        v-on:submit="$emit('latest-params', this.latest.id, this.latest.name, this.latest.limit)"
    >
      <div class="inputs">
        <label for="text" class="label1">
          To:
          <input
            type="text"
            class="contactname"
            id="text"
            placeholder="Search contact from contact list, please"
            disabled
            v-model="input1"
            :value="name"
          />
          <!-- <button class="delete">
            <i class="fa-solid fa-delete-left"></i>
          </button> -->
        </label>
        <label for="amount">
          Amount:
          <input
            type="number"
            class="amount"
            id="amount"
            v-model="input2"
            min="10"
            :max="limit"
          />
        </label>
      </div>
      <button 
      class="send"
      >
      Send
      </button>
    </form>
    <div class="history">
        <History 
        :id="transaction.id"
        :name="transaction.name"
        :sent="transaction.sent"
        :date="transaction.date"/>
    </div>
  </div>
</template>

<script>
import History from "./History.vue";
export default {
    name: "wallet",
    props: ["id", "name", "limit"],
    searched: {},
    data() {
        return {
            input1: '',
            input2: '',
            balance: 1000,
            latest: {
                id: "",
                name: "",
                limit: ""
            },
            transaction: [{
                id: '',
                name: '',
                sent: '',
                date: ''
            }]
        };
    },
    methods: {
        onSubmit() {
            if (this.balance >= amount.value){
                this.latest.id = this.id,
                this.latest.name = text.value,
                this.latest.limit = this.limit - amount.value;

                this.transaction.id = this.id,
                this.transaction.name = this.name,
                this.transaction.sent = amount.value, 
                this.transaction.date = new Date().toLocaleDateString()

                this.input1 = "";
                this.input2 = "";
                this.balance = this.balance - amount.value;
            }
        }
    },
    components: { 
        History 
    }
};
</script>

<style scoped>
.wallet {
  width: 550px;
  height: 100%;
  border-radius: 10px;
  padding: 0px 10px 10px 10px;
}
.header {
  color: rgb(100, 100, 100);
  text-align: end;
  padding: 10px 40px;
  margin-bottom: 20px;
  background: rgb(245, 245, 245);
  background: linear-gradient(
    90deg,
    rgba(245, 245, 245, 1) 40%,
    rgba(0, 0, 139, 0.7962535355939251) 90%
  );
  border-radius: 4px;
  color: gold;
  letter-spacing: 1px;
}
.balance {
  text-align: end;
  padding-right: 20px;
  font-style: italic;
  color: darkblue;
  margin-bottom: 40px;
}
.sendto {
  width: 100%;
  height: 100px;
  display: flex;
  justify-content: space-between;
  align-items: center;
}
.inputs {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: flex-end;
  gap: 10px;
  width: 77%;
}
input {
  width: 300px;
  height: 40px;
  margin-left: 10px;
  padding: 5px 10px;
  border: 1px solid rgba(0, 0, 139, 0.3);
  border-radius: 3px;
  outline: none;
  font-size: 18px;
  background-color: whitesmoke;
}
label {
  color: darkblue;
  font-size: 18px;
}
.label1 {
  position: relative;
}
.delete {
  position: absolute;
  top: 5px;
  right: 5px;
  width: 30px;
  height: 30px;
  font-size: 20px;
  color: maroon;
  border-radius: 50%;
  border: none;
  background-color: transparent;
  cursor: pointer;
}
input::-webkit-outer-spin-button,
input::-webkit-inner-spin-button {
  -webkit-appearance: none;
}
input::placeholder {
  font-size: 14px;
  color: rgba(128, 128, 128, 0.4);
}
input:disabled {
  color: black;
}
.send {
  width: 100px;
  height: 45px;
  margin-right: 10px;
  border-radius: 10px;
  background-color: rgb(0, 204, 0);
  border: none;
  color: whitesmoke;
  font-size: 20px;
  letter-spacing: 1px;
  font-family: "Bold";
  box-shadow: 0px 0px 6px 0px gray;
  cursor: pointer;
  transition: 0.2s;
}
.send:hover {
  background-color: rgb(0, 168, 0);
}
.send:active {
  box-shadow: 0px 0px 6px 0px inset rgb(108, 108, 108);
  transform: scale(0.98);
}
.history {
  border: 1px solid rgb(191, 191, 191);
  margin-top: 20px;
  width: 100%;
  height: 295px;
  border-radius: 5px;
  box-shadow: 0px 0px 6px 0px inset rgba(167, 167, 167, 0.5);
  padding: 0px 5px;
  overflow-y: scroll;
}
</style>

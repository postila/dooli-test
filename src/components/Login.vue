<template>
  <div class="wrapper">
  <input type="text" v-model="personalNo" @keyup="handleInput">
   <button class="btn" :class=" {invalid: !validPersonalNo}" :disabled="validPersonalNo">Skapa konto</button>
   <div class="box">
     <div class="boxContent">
       <h3>Har du ett konto?</h3>
       <p>
         Logga in här <img class="arrow" src="../assets/arrow_right_white.svg">
       </p>
    </div>
    <img class="account" src="../assets/account.svg">
   </div>
  </div>
</template>

<script>
export default {
  data(){
    return {
      personalNo: '',
      validPersonalNo: false
    }
  },
  methods: {
    handleInput(){
      const pattern1 = /^\d{6}-?\d{4}$/gm
      const pattern2 = /^\d{8}-?\d{4}$/gm
    
      if (pattern1.test(this.personalNo)){
        return this.validPersonalNo = true
      }
      else if (pattern2.test(this.personalNo)){
        return this.validPersonalNo = true
      } 
      else {
        return this.validPersonalNo = false
      }
    }
  }
}
</script>

<style scoped>
.wrapper {
  width: 350px;
  margin: 100px auto;
}
input {
  display: block;
  margin: 15px 0 20px 30px;
  font-size: 15px;
}

.box {
  display: grid;
  grid-template-columns: 70% 1fr;
  background: #eee;
  width: 300px;
  border:none;
  border-radius: 15px;
  box-shadow: #eee 0 0 15px 1px;
  text-align: left;
  margin: 0 auto;
  box-sizing: border-box;
  padding: 15px 0 10px 10px;
}

.btn {
  background:#22255a;
  color: white;
  padding: 12px;
  width: 300px;
  border: none;
  border-radius: 35px;
  font-size: 17px;
  font-weight: bold;
  margin-bottom: 15px; 
  cursor: pointer;
}

h3 {
  margin: 0;
  color: black;
  font-weight: 600;
}

p {
  display:grid;
  grid-template-columns: 90px 1fr;
  font-size: 14px;
  margin:0;
  margin-top: 5px;
}

.arrow {
  align-self: center;
  background: #22255a;
  border-radius: 50%;
  padding: 3.5px;
  margin-left: 4px;
  width: 0.6em;
  cursor: pointer;
}

.account {
  grid-template-columns: end;
  width: 2.8em;
  align-self: center;
  padding-left:15px;
}

.invalid {
  opacity: 0.5;
}
</style>
<template>
    <form @submit.prevent="handlesubmit">
        <label>Email:</label>
        <input type="email"  v-model="email" required>

        <label>Passwrd:</label>
        <input type="password"  v-model="password" required>
        <p class="error"> {{ passwordError }}</p>

        <label>Role</label>
        <select v-model="role">
            <option value="admin">Admin</option>
            <option value="user">User</option>
        </select>

        <label>Skills</label>
        <input type="text" v-model="tempSkill" @keyup="storeSkills">
        <p class="error"> {{ skillesError }}</p>

        <dev v-for="(skille, index) in skilles" :key="skille" class="pill">
            <span> {{ skille }} | </span> 
            <span @click="deleteSkill(index)" style="color: red;"> Delete Skill </span>
        </dev>
        
        <div class="terms">
            <input type="checkbox" v-model="terms" required>
            <label> accept terms and conditions </label>
        </div>

        <div class="terms">
            <input type="checkbox" value="mohamed" v-model="names" >
            <label> Mohamed </label>
        </div>
        <div class="terms">
            <input type="checkbox" value="ahmed" v-model="names" >
            <label> Ahmed</label>
        </div>
        <div class="terms">
            <input type="checkbox" value="ibrahime" v-model="names" >
            <label> Ibrahime </label>
        </div>

        <div class="submit">
            <button type="submit"> Create Account </button>
        </div>

    </form>

    <br>
    <p>Email : {{ email }}</p>
    <p>Password : {{ password }}</p>
    <p>Role : {{ role }}</p>
    <p>Terms : {{ terms }}</p>

    <div v-for="name in names" :key="name">
        name : {{ name }}
    </div>


</template>

<script>
export default {
    data (){
        return{
            email:'default email',
            password:'',
            role:'',
            terms:false,
            names:[],
            tempSkill:'',
            skilles: [],
            passwordError: '',
            skillesError: '',
        }
    },

    methods : {
        storeSkills (event){
            let stringText = this.tempSkill.split(',') || this.tempSkill.split('  ') ;

            if(stringText[0] && (event.key === ',' || event.key === ' ' ) ){

                if(!this.skilles.includes(stringText[0])){
                    this.skilles.push(stringText[0])
                }
                this.tempSkill = ''
                
            }
        },

        deleteSkill (index){
            this.skilles.splice(index , 1);
        },

        handlesubmit (){
            this.passwordError = this.password.length > 5 ? '' : 'The Password Field Must be greater than 6 characters'
            this.skillesError = this.skilles.length > 0 ? '' : 'You Must add one skill at least'

            if(!this.passwordError || !this.skillesError){

                console.log(this.email)
                console.log(this.password)
                console.log(this.role)
                console.log(this.skilles)
            }
        },
    }
}
</script>

<style>
form{
  max-width: 420px;
  margin: 30px auto;
  background: white;
  text-align: left;
  padding: 40px;
  border-radius: 10px ;
}

label{
  color: #aaa;
  display: inline-block;
  margin: 25px 0px 15px;
  font-size: 0.6em;
  text-transform: uppercase;
  letter-spacing: 1px;
  font-weight: bold ;

}

input, select{
  display: block;
  padding: 10px 6px;
  width: 100%;
  box-sizing: border-box;
  border: none;
  border-bottom: 1px solid #ddd;
  color: #555;
}

input[type='checkbox']{
  display: inline-block;
  width: 16px;
  margin: 0px 10px 0px 0px;
  position: relative;
  top: 5px;
}

.pill{
    display: inline-block;
    margin: 20px 10px 0 0;
    padding: 6px 12px;
    background: #eee;
    border-radius: 20px;
    font-size: 12px;
    letter-spacing: 1px;
    font-weight: bold;
    color: #777;
    cursor: pointer;
}

button{
    background: #0b6dff;
    border: 0;
    padding: 10px 20px;
    margin: 20px;
    margin-top: 20px ;
    color: white;
    border-radius: 20px ;
}

.submit{
    text-align: center;
}

.error{
    color: red;
    margin-top: 10px ;
    font-size: 0.8em;
    font-weight: bold;
}
</style>
<template>
  <div class="container">
    <form action="">
      <div class="row">
        <div class="col-xs-12 col-sm-8 offset-sm-2 col-md-6 offset-md-3">
          <h1 class="text-center">Form</h1>
          <hr>
          <div class="form-group">
            <label for="email">Email</label>
            <input 
            type="text" 
            id="email"
            class="form-control"
            :value="userData.email"
            @input="userData.email = $event.target.value"
            >
          </div>
          <div class="form-group">
            <label for="password">Password</label>
            <input 
            type="password" 
            id="password" 
            class="form-control"
            v-model="userData.password"
            >
          </div>
          <div class="form-group">
            <label for="age">Age</label>
            <input 
            type="text" 
            id="age" 
            class="form-control"
            v-model="userData.age"
            >
          </div>
        </div>
      </div>
      <div class="row">
        <div class="col-xs-12 col-sm-8-offset-sm-2 col-md-6 offset-md-3 form-group">
          <label for="message">Message</label><br>
          <textarea name="" id="message" rows="5" class="form-control" v-model="message"></textarea>
        </div>
      </div>
      <div class="row">
        <div class="col-xs-12 col-sm-8-offset-sm-2 col-md-6 offset-md-3 form-group">
          <div class="form-group">
            <label for="sendmail">
              <input 
              type="checkbox" 
              id="sendmail" 
              value="SendMail"
              v-model="sendEmail"
              > Send Mail
            </label>
            <label for="sendInfomail">
              <input 
              type="checkbox" 
              id="sendInfomail" 
              value="SendInfoMail"
              v-model="sendEmail"
              > Send InfoMail
            </label>
            <label for="cutMail">
              <input 
              type="checkbox" 
              id="cutMail" 
              value="cutMail"
              v-model="sendEmail"
              > Cut InfoMail
            </label>
          </div>
        </div>
      </div>
      <div class="row">
        <div class="col-xs-12 col-sm-8-offset-sm-2 col-md-6 offset-md-3 form-group">
          <label for="male">
            <input 
            type="radio" 
            id="male" 
            value="Male"
            v-model="gender"
            > Male
          </label>
          <label for="female">
            <input 
            type="radio" 
            id="female" 
            value="Female"
            v-model="gender"
            > Female
          </label>
        </div>
      </div>
      <div class="row">
        <div class="col-xs-12 col-sm-8-offset-sm-2 col-md-6 offset-md-3 form-group">
          <label for="priority">Priority</label>
          <select name="" 
          id="priority" 
          class="form-control"
          v-model="selectedPriority"
          >
             <option 
             v-for="item in priorities" 
             :key="item">{{ item }}</option>
          </select>
        </div>
      </div>
      <div class="row">
        <div class="col-xs-12 col-sm-8-offset-sm-2 col-md-6 offset-md-3 form-group">
          <label for="switched">Switched: </label>
          <app-custom-control v-model="dataSwitch"></app-custom-control>
        </div>
      </div>
      <hr>
      <div class="row">
        <div class="col-xs-12 col-sm-8-offset-sm-2 col-md-6 offset-md-3 form-group">
          <button 
          class="btn btn-primary"
          @click.prevent="submited"
          >Submit</button>
        </div>
      </div>
      </form>
      <hr>
      <div class="row" v-if="isSubmit">
        <div class="col-xs-12 col-sm-8-offset-sm-2 col-md-6 offset-md-3">
         <div class="panel panel-default">
           <div class="panel-heading">
             <h4>Your Data</h4>
           </div>
           <div class="panel-body">
             <p>Mail: {{ userData.email }}</p>
             <p>Password: {{ userData.password }}</p>
             <p>Age: {{ userData.age }} </p>
             <p style="white-space: pre">Message: {{ message }}</p>
             <p><strong>Send Mail? </strong></p>
             <ul>
               <li v-for="item in sendEmail" :key="item">{{ item }}</li>
             </ul>
             <p>Gender: {{ gender }}</p>
             <p>Priority: {{ selectedPriority }}</p>
             <p>Switched: {{ dataSwitch }}</p>
           </div>
         </div>
        </div>
      </div>
  </div>
</template>

<script>
import CustomControl from './components/CustomControl';
export default {
  data() {
    return {
      userData: {
        email: '',
        password: '',
        age: 0
      },
      message: 'something...',
      sendEmail: [],
      gender: 'Male',
      priorities: ['High', 'Medium', 'Low'],
      selectedPriority: 'Medium',
      dataSwitch: true,
      isSubmit: false
    }
  },
  methods: {
    submited() {
      this.isSubmit = true;
    }
  },
  components: {
    appCustomControl: CustomControl
  }
}
</script>

<style>

</style>

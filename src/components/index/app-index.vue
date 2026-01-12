<template>
    <div>
        <main class="main_content">
          <div class="container">
            <div class="row">
              <div class="col-md-12">
                <div class="from_content">
                  <form action="#">
                    <div class="row">
                      <div class="col-md-12">
                        <div class="main_title text-center">
                          <h4>Technology & Online Learning Survey</h4>
                        </div>
                      </div>
                      <div class="col-md-12">
                        <div class="form_item">
                          <label>Full Name</label>
                          <input v-model="formData.name" class="form-control" type="text" placeholder="Hossain Zumon"/>
                          <div class="errors_required" v-if="errors.name">{{ errors.name }}</div>
                        </div>
                      </div>
                      <div class="col-md-12">
                        <div class="form_item">
                          <label>Email Address</label>
                          <input v-model="formData.email" class="form-control" type="email" placeholder="zumonhossain100@gmail.com"/>
                          <div class="errors_required" v-if="errors.email">{{ errors.email }}</div>
                        </div>
                      </div>
                      <div class="col-md-12">
                        <div class="form_item">
                          <label>Age</label>
                          <input v-model="formData.age" class="form-control" type="number" placeholder="27"/>
                        </div>
                      </div>
                      <!-- <div class="col-md-12">
                        <div class="form_item">
                          <label>Gender</label>
                          <select v-model="formData.gender" class="form-control">
                            <option value="">Select Gender</option>
                            <option>Male</option>
                            <option>Female</option>
                            <option>Other</option>
                          </select>
                        </div>
                      </div> -->
                      <div class="col-md-12">
                        <div class="form_item">
                          <label>Gender</label>
                          <select class="form-control">
                            <option value="">Select Gender</option>
                            <option v-for="gender in genders" :key="gender">{{ gender }}</option>
                          </select>
                        </div>
                      </div>
                      <div class="col-md-12">
                        <div class="form_item">
                          <label>Field of Study</label>
                          <input type="text" v-model="formData.studyField">
                        </div>
                      </div>
                      <div class="col-md-12">
                        <div class="form_item">
                          <label>Daily Study Hours</label>
                          <input type="range" min="1" max="12" v-model="formData.hours">
                          <input type="number" v-model="formData.hours">
                        </div>
                      </div>
                      <div class="col-md-12">
                        <div class="form_item_checkbox">
                          <label>Preferred Device</label>
                          <div class="form-check">
                            <input value="Computer" v-model="formData.device" class="form-check-input" type="radio" name="flexRadioDefault" id="flexRadioDefault1">
                            <label class="form-check-label" for="flexRadioDefault1">
                              Computer
                            </label>
                          </div>
                          <div class="form-check">
                            <input value="Mobile" v-model="formData.device" class="form-check-input" type="radio" name="flexRadioDefault" id="flexRadioDefault2">
                            <label class="form-check-label" for="flexRadioDefault2">
                              Mobile
                            </label>
                          </div>
                        </div>
                      </div>
                      <div class="col-md-12">
                        <div class="form_item_checkbox">
                          <label>Online Platforms Used</label>
                          <div class="form-check">
                            <input value="Zoom" v-model="platforms" class="form-check-input" type="checkbox" id="flexCheckZoom">
                            <label class="form-check-label" for="flexCheckZoom">
                              Zoom
                            </label>
                          </div>
                          <div class="form-check">
                            <input value="GoogleMeet" v-model="platforms" class="form-check-input" type="checkbox" id="flexCheckGoogleMeet">
                            <label class="form-check-label" for="flexCheckGoogleMeet">
                              Google Meet
                            </label>
                          </div>
                          <div class="form-check">
                            <input value="MSTeams" v-model="platforms" class="form-check-input" type="checkbox" id="flexCheckMSTeams">
                            <label class="form-check-label" for="flexCheckMSTeams">
                              MS Teams
                            </label>
                          </div>
                        </div>
                      </div>
                      <div class="col-md-12">
                        <div class="form_item_checkbox_notify">
                          <label>Enable Notifications</label>
                          <div class="form-check form-switch">
                            <input v-model="formData.notify" class="form-check-input" type="checkbox" id="flexSwitchCheckChecked">
                          </div>
                          <span>{{ formData.notify ? 'ON' : 'OFF' }}</span>
                        </div>
                      </div>
                      <div class="col-md-12">
                        <div class="form_item">
                          <label>Submission Date</label>
                          <input v-model="formData.date" class="form-control" type="date">
                        </div>
                      </div>
                      <div class="col-md-12">
                        <div class="form_item">
                          <label>Overall Satisfaction (Badge Rating)</label>
                          <ul>
                            <li>
                              <span @click="ratingSelect('Bronze')" class="bronze">Bronze 🥉</span>
                            </li>
                            <li>
                              <span @click="ratingSelect('Silver')" class="silver">Silver 🥈</span>
                            </li>
                            <li>
                              <span @click="ratingSelect('Gold')" class="gold">Gold 🥇</span>
                            </li>
                            <li>
                              <span @click="ratingSelect('Platinum')" class="platinum">Platinum 💎</span>
                            </li>
                          </ul>
                        </div>
                      </div>
                      <div class="col-md-12">
                        <div class="form_item">
                          <label>Audio Clip</label>
                          <audio controls>
                            <source src="https://www.w3schools.com/html/horse.mp3">
                          </audio>
                        </div>
                      </div>
                      <div class="col-md-12">
                        <div class="form_item">
                          <label>Comments</label>
                          <textarea v-model="comments" class="form-control"></textarea>
                        </div>
                      </div>
                      <div class="col-md-12">
                          <button @click.prevent="submitForm" class="btn_submit">Submit</button>
                          <button @click.prevent="clearForm" class="btn_clear">Clear</button>
                      </div>
                    </div>
                  </form>
                </div>
              </div>
              <div class="col-md-12" v-if="isSubmiTted">
                  <div class="output_item">
                    <label>Submitted Survey Data</label>
                    <ul>
                      <li>Full Name: {{ formData.name }}</li>
                      <li>Email: {{ formData.email }}</li>
                      <li>Age: {{ formData.age }}</li>
                      <li>Gender: {{ formData.gender }}</li>
                      <li>Device: {{ formData.device }}</li>
                      <li>Notifications: {{ formData.notify ? 'ON' : 'OF' }}</li>
                      <li>Date: {{ formData.date }}</li>
                      <li>Daily Study Hours: {{ formData.hours }}</li>
                      <li>Field of Study: {{ formData.studyField }}</li>
                      <li>Overall Satisfaction: {{ formData.rating }}</li>
                      <li>
                        Online Platforms Used:
                        <ul>
                          <li v-for="platform in platforms" :key="platform">{{ platform }}</li>
                        </ul>
                      </li>
                      <li style="white-space: pre-line;">Comments: {{ comments }}</li>
                    </ul>
                  </div>
              </div>
            </div>
          </div>
        </main>
    </div>
</template>

<script>
  export default {
    name: 'AppIndex',
    data(){
      return {
        formData: {
          name: '',
          email: '',
          age: '',
          // gender: '',
          date: '',
          device: '',
          notify: false,
          hours: 1,
          studyField: '',
          rating: '',
        },
        comments: '',
        platforms: [],
        genders: ['Male', 'Female', 'Other'],
        isSubmiTted: false,
        errors: {}
      }
    },
    methods: { 
      ratingSelect(rating){
        this.formData.rating = rating;  
      },
      validateForm(){
        this.errors = {};
        if(!this.formData.name){
          this.errors.name = 'Full Name is required.';
        }
        if(!this.formData.email){
          this.errors.email = 'Email Address is required.';
        } else if(!/\S+@\S+\.\S+/.test(this.formData.email)){
          this.errors.email = 'Email Address is invalid.';
        }
      },
      submitForm(){
        this.validateForm();
        if(Object.keys(this.errors).length === 0){
          this.isSubmiTted = true;
        }
      },
      clearForm(){
        this.formData = {
          name: '',
          email: '',
          age: '',
          // gender: '',
          date: '',
          device: '',
          notify: false,
          hours: 1,
          studyField: '',
          rating: '',
        },
        this.comments = '';
        this.platforms = [];
        this.genders = ['Male', 'Female', 'Other'];
        this.isSubmiTted = false;
        this.errors = {};
      }
    }
  }
</script>

<style scoped>
  .errors_required{
    color: red;
    margin-top: 1px;
  }
  .form_item input{
    width: 100%;
    padding: 10px;
    margin-top: 5px;
    border: 1px solid #ccc;
    border-radius: 5px;
  }
</style>
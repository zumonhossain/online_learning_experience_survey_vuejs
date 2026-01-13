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
                          <label>Full Name <span class="r_star">*</span></label>
                          <input v-model="formData.name" class="form-control" type="text" placeholder="Enter your name"/>
                          <div class="errors_required" v-if="errors.name">{{ errors.name }}</div>
                        </div>
                      </div>
                      <div class="col-md-12">
                        <div class="form_item">
                          <label>Student ID</label>
                          <input v-model="formData.studentId" class="form-control" type="text" placeholder="Enter your student id"/>
                          <div class="errors_required" v-if="errors.studentId">{{ errors.studentId }}</div>
                        </div>
                      </div>
                      <div class="col-md-12">
                        <div class="form_item">
                          <label>Email Address <span class="r_star">*</span></label>
                          <input v-model="formData.email" class="form-control" type="email" placeholder="Enter your email"/>
                          <div class="errors_required" v-if="errors.email">{{ errors.email }}</div>
                        </div>
                      </div>
                      <div class="col-md-12">
                        <div class="form_item">
                          <label>Age</label>
                          <input v-model="formData.age" class="form-control" type="number" placeholder="Enter your age"/>
                          <div class="errors_required" v-if="errors.age">{{ errors.age }}</div>
                        </div>
                      </div>
                      <div class="col-md-12">
                        <div class="form_item">
                          <label>Gender</label>
                          <select v-model="formData.gender" class="form-control">
                            <option value="">Select Gender</option>
                            <option>Male</option>
                            <option>Female</option>
                            <option>Other</option>
                          </select>
                          <div class="errors_required" v-if="errors.gender">{{ errors.gender }}</div>
                        </div>
                      </div>
                      <div class="col-md-12">
                        <div class="form_item">
                          <label>Field of Study</label>
                          <input class="form-control" type="text" v-model="formData.studyField" placeholder="Enter field of study">
                          <div class="errors_required" v-if="errors.studyField">{{ errors.studyField }}</div>
                        </div>
                      </div>
                      <div class="col-md-12">
                        <div class="form_item">
                          <label>Daily Study Hours</label>
                          <input type="range" min="1" max="12" v-model="formData.hours" placeholder="Enter daily study hours">
                          <input class="form-control" type="number" v-model="formData.hours">
                          <div class="errors_required" v-if="errors.hours">{{ errors.hours }}</div>
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
                          <div class="d-flex align-items-center">
                            <div class="form-check form-switch">
                              <input v-model="formData.notify" class="form-check-input" type="checkbox" id="flexSwitchCheckChecked">
                            </div>
                            <span>{{ formData.notify ? 'ON' : 'OFF' }}</span>
                          </div>
                        </div>
                      </div>
                      <div class="col-md-12">
                        <div class="form_item">
                          <label>Submission Date</label>
                          <input v-model="formData.date" class="form-control" type="date">
                          <div class="errors_required" v-if="errors.date">{{ errors.date }}</div>
                        </div>
                      </div>
                      <div class="col-md-12">
                        <div class="form_item">
                          <label>Study Mode (Online / Offline / Hybrid)</label>
                          <input v-model="formData.studyMode" class="form-control" type="text" placeholder="Enter your study mode">
                          <div class="errors_required" v-if="errors.studyMode">{{ errors.studyMode }}</div>
                        </div>
                      </div>
                      <div class="col-md-12">
                        <div class="form_item">
                          <label>Internet Quality</label>
                          <input v-model="formData.internetQuality" class="form-control" type="text" placeholder="Enter internet quality">
                          <div class="errors_required" v-if="errors.internetQuality">{{ errors.internetQuality }}</div>
                        </div>
                      </div>
                      <div class="col-md-12">
                        <div class="form_item">
                          <label>Favorite Learning Platform</label>
                          <input v-model="formData.favoritePlatform" class="form-control" type="text" placeholder="Enter favorite learning platform">
                          <div class="errors_required" v-if="errors.favoritePlatform">{{ errors.favoritePlatform }}</div>
                        </div>
                      </div>
                      <div class="col-md-12">
                        <div class="form_item">
                          <label>Future Learning Goal</label>
                          <input v-model="formData.futureLearningGoal" class="form-control" type="text" placeholder="Enter future learning goal">
                          <div class="errors_required" v-if="errors.futureLearningGoal">{{ errors.futureLearningGoal }}</div>
                        </div>
                      </div>
                      <div class="col-md-12">
                        <div class="form_item">
                          <label>Motivation Level</label>
                          <input v-model="formData.motivationLevel" class="form-control" type="text" placeholder="Enter motivation level">
                          <div class="errors_required" v-if="errors.motivationLevel">{{ errors.motivationLevel }}</div>
                        </div>
                      </div>
                      <div class="col-md-12">
                        <div class="form_item base_rating">
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
                          <textarea v-model="comments" class="form-control" style="height: 100px" placeholder="Enter your comments"></textarea>
                          <div class="errors_required" v-if="errors.comments">{{ errors.comments }}</div>
                        </div>
                      </div>
                      <div class="col-md-12">
                          <div class="button_group">
                            <button @click.prevent="submitForm" class="btn_submit">Submit</button>
                            <button @click.prevent="clearForm" class="btn_clear">Clear</button>
                          </div>
                      </div>
                    </div>
                  </form>
                </div>
              </div>
            </div>
          </div>
          <div class="container">
            <div class="row">
              <div class="col-md-12">
                <div class="output_show">
                  <h5>Submitted Survey Data</h5>
                  <div class="row">
                    <div class="col-md-12" v-if="isSubmiTted">
                      <div class="output_item pt-5">
                        <textarea
                          readonly
                          class="form-control"
                          rows="18"
                          v-model="formData.jsonOutput">
                        </textarea>
                      </div>
                    </div>
                  </div>
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
          studentId: '',
          email: '',
          age: '',
          gender: '',
          date: '',
          device: '',
          notify: false,
          hours: 1,
          studyField: '',
          studyMode: '',
          internetQuality: '',
          favoritePlatform: '',
          futureLearningGoal: '',
          motivationLevel: '',
          rating: '',
          jsonOutput: ''
        },
        comments: '',
        platforms: [],
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
        if(!this.formData.studentId){
          this.errors.studentId = 'Student ID is required.';
        }
        if(!this.formData.age){
          this.errors.age = 'Age is required.';
        } else if(this.formData.age <= 0){
          this.errors.age = 'Age must be a positive number.';
        }
        if(!this.formData.gender){
          this.errors.gender = 'Gender is required.';
        }
        if(!this.formData.studyField){
          this.errors.studyField = 'Study Field is required.';
        }
        if(!this.formData.hours){
          this.errors.hours = 'Hours Per Week is required.';
        } else if(this.formData.hours <= 0){
          this.errors.hours = 'Hours Per Week must be a positive number.';
        }
        if(!this.formData.date){
          this.errors.date = 'Date is required.';
        }
        if(!this.formData.studyMode){
          this.errors.studyMode = 'Study Mode is required.';
        }
        if(!this.formData.internetQuality){
          this.errors.internetQuality = 'Internet Quality is required.';
        }
        if(!this.formData.favoritePlatform){
          this.errors.favoritePlatform = 'Favorite Learning Platform is required.';
        }
        if(!this.formData.futureLearningGoal){
          this.errors.futureLearningGoal = 'Future Learning Goal is required.';
        }
        if(!this.formData.motivationLevel){
          this.errors.motivationLevel = 'Motivation Level is required.';
        }
        if(!this.comments){
          this.errors.comments = 'Comments are required.';
        }
      },
      submitForm(){
      this.validateForm();

      if(Object.keys(this.errors).length > 0){
        this.isSubmiTted = false;
        this.formData.jsonOutput = '';
        return;
      }

      this.isSubmiTted = true;

      this.formData.jsonOutput = `
        Full Name : ${this.formData.name}
        Student ID : ${this.formData.studentId}
        Email Address : ${this.formData.email}
        Age : ${this.formData.age}
        Gender : ${this.formData.gender}
        Date : ${this.formData.date}
        Device : ${this.formData.device}
        Notify Me : ${this.formData.notify ? 'Yes' : 'No'}
        Hours Per Week : ${this.formData.hours}
        Study Field : ${this.formData.studyField}
        Study Mode : ${this.formData.studyMode}
        Internet Quality : ${this.formData.internetQuality}
        Favorite Learning Platform : ${this.formData.favoritePlatform}
        Future Learning Goal : ${this.formData.futureLearningGoal}
        Motivation Level : ${this.formData.motivationLevel}
        Rating : ${this.formData.rating}
        Comments : ${this.comments || ''}
        `+ (this.platforms.length ? `Online Platforms Used : ${this.platforms.join(', ')}` : 'Online Platforms Used : None');
      },
      clearForm(){
        this.formData = {
          name: '',
          studentId: '',
          email: '',
          age: '',
          gender: '',
          date: '',
          device: '',
          notify: false,
          hours: 1,
          studyField: '',
          studyMode: '',
          internetQuality: '',
          favoritePlatform: '',
          futureLearningGoal: '',
          motivationLevel: '',
          rating: '',
        },
        this.comments = '';
        this.platforms = [];
        this.isSubmiTted = false;
        this.errors = {};
      }
    }
  }
</script>

<style scoped>
  .r_star{
    color: red;
  }
  .errors_required{
    color: red;
    margin-top: 1px;
  }
  .form_item,
  .form_item_checkbox_notify,
  .form_item_checkbox {
      margin-bottom: 15px;
  }
  .form_item label,
  .form_item_checkbox_notify label,
  .form_item_checkbox label {
      font-weight: 600;
      display: inline;
  }
  .form_item input{
    width: 100%;
    padding: 10px;
    margin-top: 2px;
    border: 1px solid #ccc;
    border-radius: 5px;
  }
  .from_content {
      background-color: #dddddd;
      padding: 50px;
  }
  .form_item_checkbox .form-check label,
  .form_item_checkbox_notify .form-check label,
  .form_item_checkbox_notify input,
  .form_item_checkbox input {
      cursor: pointer;
      display: block;
      font-weight: 400;
  }
  .main_title  h4 {
      font-size: 30px;
      font-weight: 600;
      margin-bottom: 50px;
  }
  .base_rating ul{
      padding: 0;
      margin: 0;
      margin-top: 10px;
  }
  .base_rating ul li{
      list-style: none;
      display: inline-block;
      margin-right: 10px;
      cursor: pointer;
      transition: all 0.3s ease;
      border: 1px solid #584040;
      border-radius: 4px;
      padding: 3px 10px;
  }
  .base_rating ul li:hover{
      transform: scale(1.1);
  }
  .button_group {
      margin-top: 30px;
  }
  .btn_submit {
      width: 100%;
      border: none;
      background-color: #000000;
      color: #ffffff;
      font-weight: 600;
      text-transform: capitalize;
      font-size: 16px;
      padding: 8px 0px;
      border-radius: 5px;
      margin-bottom: 10px;
      transition: all 0.3s ease;
  }
  .btn_submit:hover {
      color: red;
  }
  .btn_clear {
      width: 100%;
      border: none;
      background-color: red;
      color: #ffffff;
      font-weight: 600;
      text-transform: capitalize;
      font-size: 16px;
      padding: 8px 0px;
      border-radius: 5px;
      transition: all 0.3s ease;
  }
  .btn_clear:hover {
      color: #000000;
  }
  .output_show {
      border: 2px solid #dddddd;
      padding: 50px;
      border-radius: 5px;
      margin-top: 20px;
      margin-bottom: 50px;
  }
  .output_show h5 {
      margin: 0;
      text-align: center;
      font-weight: 600;
      font-size: 22px;
  }
  .output_item li {
      margin-bottom: 8px;
      display: block;
  }
  .output_item li:last-child {
      margin-bottom: 0px;
  }
  .output_item textarea {
      height: 300px;
      overflow-y: auto;
  }
  .form_item audio {
      display: block;
      margin-top: 10px;
  }
</style>
<template>
    <div>
        <header class="header_area" style="background-image: url('https://i.ibb.co/KjJLHH2K/1.jpg');">
          <div class="header_overlay"></div>
          <div class="container">
            <div class="row">
              <div class="col-md-12">
                <div class="header_content text-center">
                  <div class="header_content_inner">
                    <h1>Full Name : Hossain Zumon <span>|</span> Student ID : M25W7480</h1>
                    <h4>Current Date & Time: {{ currentTime }}</h4>
                  </div>
                </div>
              </div>
            </div>
          </div>
          <div class="mascot_animation">
            <img src="https://i.ibb.co/XrM6FGKw/1.gif" alt="Mascot"/>
          </div>
        </header>
    </div>
</template>

<script>
  export default {
    data() {
      return {
        currentTime: '',
        timer: null
      };
    },
    mounted() {
      this.updateTime();
      this.timer = setInterval(this.updateTime, 1000);
    },
    beforeUnmount() {
      clearInterval(this.timer);
    },
    methods: {
      updateTime() {
        const now = new Date();

        const options = {
          weekday: 'long',
          year: 'numeric',
          month: 'long',
          day: 'numeric',
          hour: 'numeric',
          minute: '2-digit',
          second: '2-digit',
          hour12: true
        };

        const formatted = now.toLocaleString('en-US', options);

        this.currentTime = formatted.replace(',', ' at');
      }
    }
  };
</script>

<style scoped>
  .header_area {
      width: 100%;
      height: 250px;
      background-size: cover;
      background-repeat: no-repeat;
      background-position: center;
      position: relative;
  }
  .header_overlay::after {
      content: '';
      position: absolute;
      top: 0;
      left: 0;
      right: 0;
      bottom: 0;
      background-color: #000000;
      opacity: .6;
  }
  .header_content {
      display: flex;
      align-items: center;
      justify-content: center;
      height: 250px;
      position: relative;
      z-index: 1;
  }
  .header_content_inner {
      color: #ffffff;
  }
  .header_content_inner h1 {
      font-size: 35px;
      margin-bottom: 20px;
  }
  .header_content_inner h4 {
      font-size: 20px;
  }
  .mascot_animation img {
      width: 150px;
      height: 150px;
      position: absolute;
      bottom: -50px;
      left: 125px;
      border-radius: 100%;
  }
</style>
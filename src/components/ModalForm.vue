<template>
  <transition name="modal">
    <div class="modal-mask">
      <div class="modal-wrapper">
        <div class="modal-container" transition='modal'>
          <div class="modal-header">
            <h3>Say hello!</h3>
            <span class='sub-header'>I'm always up for a chat</span>
          </div>
          <div class="modal-body">
            <transition name='mail-sending' mode='out-in'>
              <div class='form' v-if="sendState === 'start'" key='start'> <!-- the fucking key is kind of important for transitions -->
                <input class='form-input email' v-validate="'required|email'" :class="{ 'is-danger': errors.has('email')}" name='email' type='email' v-model='mailData.senderEmail' placeholder="Your email"></input>
                <span class='form-error' v-show="errors.has('email')">You must provide an email.</span>
                <textarea class='form-input message' v-validate="'required'" :class="{ 'is-danger': errors.has('message')}" name='message' v-model='mailData.message' placeholder="Your message"></textarea>
                <span class='form-error' v-show="errors.has('message')">Your message can not be empty.</span>
                <input type="text" v-model='mailData._gotcha' name="_gotcha" style="display:none" />
              </div>
              <div class='result spinner' v-if="sendState === 'wait'" key='wait'>
                <PulseLoader color='#20BF55'/>
              </div>
              <div class='result success' v-if="sendState === 'success'" key='success'>
                <i class='fa fa-4x fa-check'></i>
                <span>Message sent! I'll get in touch shortly.</span>
              </div>
            </transition>
          </div>
          <div class="modal-footer">
            <button class="modal-default-button" @click="$emit('close')">
              DISMISS
            </button>
            <button class="modal-default-button" @click="validateAndSubmit()">
              SEND
            </button>
          </div>
        </div>
      </div>
    </div>
  </transition>
</template>

<script>
import axios from 'axios'
import PulseLoader from 'vue-spinner/src/PulseLoader.vue'

export default {
  data () {
    return {
      sendEmail: 'http://formspree.io/luis.agm24@gmail.com',
      mailData: {
        message: '',
        senderEmail: '',
        _gotcha: 'w'
      },
      sendState: 'start' // start -> wait -> success
    }
  },
  methods: {
    closeModal () {
      console.log('closingforevar')
      this.$emit('close')
    },
    sendMail () {
      return axios({
        method: 'POST',
        url: this.sendEmail,
        data: {
          _gotcha: this.mailData._gotcha,
          _subject: `Message from ${this.mailData.senderEmail}`,
          message: this.mailData.message,
          email: this.mailData.senderEmail
        }
      })
    },
    validateAndSubmit () {
      this.$validator.validateAll()
      if (!this.errors.any()) {
        this.sendState = 'wait'
        this.sendMail().then((response) => {
          console.log('Email sent: ', response)
          this.sendState = 'success'
          setTimeout(this.closeModal, 1800)
        })
      }
    }
  },
  components: { PulseLoader }
}
</script>

<style lang='scss' scoped>

.modal-header {
  h3 {
    margin-top: 0;
    margin-bottom: 10px;
    color: $primary;
    font-weight: 600;
    font-size: responsive 24px 38px;
  }
  .sub-header {
    font-style: italic;
    font-weight: 600;
    font-size: responsive 12px 18px;
    color: $light-gray;
  }
}

/***** Form Content ********/

.modal-body {
  min-height: 150px;

  .result {
    display: flex;
    justify-content: center;
    flex-flow: column;
    align-items: center;
    i {
      align-self: center;
      color: $primary;
    }

  }
  .form {
    margin: 20px 0;
    display: flex;
    flex-flow: column;
    width: 100%;
    .form-input {
      box-sizing: border-box;
      width: 100%;
      font-family: 'Roboto', sans-serif;
      font-size: responsive 12px 14px;
      height: 35px;
      margin: 5px 0px;
      border-radius: 2px;
      border: none;
      border-bottom: 2px solid $dark-gray;
      padding: 0 10px;

      &.message {
        height: 85px;
        padding-top: 10px;        
      }

      &.is-danger {
        box-shadow: 0px 0px 4px red;
      }
    }
    .form-error {      
      color: red;
      font-family: 'Raleway', sans-serif;
    }
  }
}

.modal-footer{
  display: flex;
  flex-flow: row nowrap;
  justify-content: flex-end;

  .modal-default-button {
    cursor: pointer;
    color: $white;
    align-self: flex-end;
    background-color: $primary;
    font-family: 'Roboto',sans-serif;    
    font-size: responsive 12px 14px;
    font-weight: 700;
    border: none;
    margin: 5px;
    height: 50px;
    min-width: 90px;
    border-radius: 2px;
  }
}
/****** Form Transition ****/
.mail-sending-enter-active, .mail-sending-leave-active {
  transition: opacity .5s
}
.mail-sending-enter, .mail-sending-leave-to /* .fade-leave-active in <2.1.8 */ {
  opacity: 0
}

/****** Modal Transition ****/

.modal-enter {
  opacity: 0;
}

.modal-leave-active {
  opacity: 0;
}

.modal-enter .modal-container,
.modal-leave-active .modal-container {
  -webkit-transform: scale(1.1);
  transform: scale(1.1);
}

/********* General boring modal stuff ******/
  
.modal-mask {
  position: fixed;
  z-index: 9998;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, .5);
  display: table;
  transition: opacity .3s ease;
}

.modal-wrapper {
  z-index: 9999;
  display: table-cell;
  vertical-align: middle;
}

.modal-container {
  max-width: 450px;
  margin: 0px auto;
  padding: 20px 30px;
  background-color: #fff;
  border-radius: 2px;
  box-shadow: 0 2px 8px rgba(0, 0, 0, .33);
  transition: all .3s ease;
  font-family: 'Raleway', Arial, sans-serif;
}

</style>

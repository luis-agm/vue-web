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
            <input class='form-input email' type='email' v-model='senderEmail' placeholder="Your email"></input>
            <textarea class='form-input message' v-model='message' placeholder="Your message"></textarea>
            <input type="text" v-model='_gotcha' name="_gotcha" style="display:none" />
          </div>
          <div class="modal-footer">
            <button class="modal-default-button" @click="$emit('close')">
              DISMISS
            </button>
            <button class="modal-default-button" @click="sendMail()">
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

export default {
  data () {
    return {
      sendEmail: 'http://formspree.io/luis.agm24@gmail.com',
      message: '',
      senderEmail: '',
      _gotcha: ''
    }
  },
  methods: {
    sendMail () {
      axios({
        method: 'POST',
        url: this.sendEmail,
        data: {
          _gotcha: this._gotcha,
          _subject: `Message from ${this.senderEmail}`,
          message: this.message,
          email: this.senderEmail
        }
      })
    }
  }
}
</script>

<style lang='scss' scoped>
  
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
  width: 450px;
  margin: 0px auto;
  padding: 20px 30px;
  background-color: #fff;
  border-radius: 2px;
  box-shadow: 0 2px 8px rgba(0, 0, 0, .33);
  transition: all .3s ease;
  font-family: 'Raleway', Arial, sans-serif;
}

.modal-header {
  h3 {
    margin-top: 0;
    margin-bottom: 10px;
    color: $primary;
    font-weight: 500;
  }
  .sub-header {
    font-style: italic;
    font-weight: 400;
    font-size: 14px;
    color: $light-gray;
  }
}

.modal-body {
  margin: 20px 0;
  display: flex;
  flex-flow: column;
  max-width: 320px;
  .form-input {
    max-width: 80%;
    font-family: 'Roboto', sans-serif;
    height: 24px;
    margin: 5px;
    border-radius: 2px;
    border: 1px solid $light-gray;
    padding: 5px 5px;
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
    font-size: 14px;
    font-weight: 500;
    border: none;
    margin: 5px;
    height: 50px;
    min-width: 90px;
    border-radius: 2px;
  }
}


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
</style>

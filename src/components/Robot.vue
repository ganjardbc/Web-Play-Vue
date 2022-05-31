<template>
    <div :class="`container ${visibleMenu && 'show'}`">
      <div class="float-menu">
        <button
          :class="`button ${visibleMenu && 'active'}`" 
          @click="visibleMenu = !visibleMenu">
          MENU 
        </button>
      </div>

      <div class="container-left">
        <div :class="`robot-container ${!powerStatus && 'shutdown'}`">
          <div :class="`robot-wrapper ${wrapperAnimation && 'active'}`">
            <div class="robot-head">
              <div 
                :class="`robot-face ${facePosition}`" 
                @click="changePowerStatus">
                <div :class="`robot-eyes ${expression} ${eyePosition}`">
                  <div 
                    :class="`eye ${eyeAnimation && 'eye-animation'}`" 
                    id="eye-left"></div>
                  <div 
                    :class="`eye ${eyeAnimation && 'eye-animation'}`" 
                    id="eye-right"></div>
                </div>
              </div>
            </div>
            <div :class="`robot-body ${expression}`">
              <div 
                :class="`robot-hand ${expression}`" 
                id="hand-left"></div>
              <div 
                :class="`robot-hand ${expression}`" 
                id="hand-right"></div>
            </div>
          </div>
        </div>
      </div>

      <div class="container-right">
        <div class="menu-wrapper">
          <div>MENU</div>
          <button
            :class="`button`" 
            @click="visibleMenu = !visibleMenu">
            CLOSE MENU 
          </button>
        </div>
        <div class="menu-wrapper">
          <div>POWER</div>
          <button 
            :class="`button ${powerStatus && 'active'}`" 
            @click="changePowerStatus">
            {{ powerStatus ? 'SHUT DOWN' : 'POWER UP' }}
          </button>
        </div>
        <div class="menu-wrapper">
          <div>ANIMATIONS</div>
          <button 
            :disabled="!powerStatus"
            :class="`button ${wrapperAnimation && 'active'}`" 
            @click="wrapperAnimation = !wrapperAnimation">
            BODY   
          </button>
          <button 
            :disabled="!powerStatus"
            :class="`button ${eyeAnimation && 'active'}`" 
            @click="eyeAnimation = !eyeAnimation">
            EYES
          </button>
        </div>
        <div class="menu-wrapper">
          <div>EXPRESSIONS</div>
          <button 
            :disabled="!powerStatus"
            :class="`button ${expression === 'normal' && 'active'}`" 
            @click="expression = 'normal'">
            NORMAL  
          </button>
          <button 
            :disabled="!powerStatus"
            :class="`button ${expression === 'angry' && 'active'}`" 
            @click="expression = 'angry'">
            ANGRY 
          </button>
          <button 
            :disabled="!powerStatus"
            :class="`button ${expression === 'supprised' && 'active'}`" 
            @click="expression = 'supprised'">
            SUPPRISED
          </button>
          <button 
            :disabled="!powerStatus"
            :class="`button ${expression === 'mood' && 'active'}`" 
            @click="expression = 'mood'">
            MOOD
          </button>
          <button 
            :disabled="!powerStatus"
            :class="`button ${expression === 'happy' && 'active'}`" 
            @click="expression = 'happy'">
            HAPPY
          </button>
        </div>
        <div class="menu-wrapper">
          <div>EYE POSITION</div>
          <button 
            :disabled="!powerStatus"
            :class="`button ${eyePosition === 'look-ahead' && 'active'}`" 
            @click="eyePosition = 'look-ahead'">
              AHEAD
          </button>
          <button 
            :disabled="!powerStatus"
            :class="`button ${eyePosition === 'look-up' && 'active'}`" 
            @click="eyePosition = 'look-up'">
              UP
          </button>
          <button 
            :disabled="!powerStatus"
            :class="`button ${eyePosition === 'look-down' && 'active'}`" 
            @click="eyePosition = 'look-down'">
              DOWN
          </button>
        </div>
        <div class="menu-wrapper">
          <div>FACE POSITION</div>
          <button 
            :disabled="!powerStatus"
            :class="`button ${facePosition === 'look-ahead' && 'active'}`" 
            @click="facePosition = 'look-ahead'">
              AHEAD
          </button>
          <button 
            :disabled="!powerStatus"
            :class="`button ${facePosition === 'look-left' && 'active'}`" 
            @click="facePosition = 'look-left'">
              LEFT
          </button>
          <button 
            :disabled="!powerStatus"
            :class="`button ${facePosition === 'look-right' && 'active'}`" 
            @click="facePosition = 'look-right'">
              RIGHT
          </button>
        </div>
      </div>
    </div>
</template>

<script>
export default {
  data() {
    return {
      visibleMenu: false,
      powerStatus: false,
      wrapperAnimation: false,
      eyeAnimation: false,
      autoExpression: false,
      eyePosition: 'look-ahead',
      facePosition: 'look-ahead',
      expression: 'normal',
      dataExpression: ['normal', 'angry']
    }
  },
  mounted() {
    // this.onAutomateExpression()
  },
  methods: {
    onAutomateExpression() {
      var i = 0
      setInterval(() => {
        i += 1
        if (i == this.dataExpression.length) {
          i = 0
        }
        this.expression = this.dataExpression[i]
      }, 3000)
    },
    changePowerStatus() {
      if (this.powerStatus) {
        this.powerStatus = false
        this.wrapperAnimation = false 
        this.eyeAnimation = false 
      } else {
        this.powerStatus = true 
        this.wrapperAnimation = true 
        this.eyeAnimation = true 
      }
    }
  }
}
</script>
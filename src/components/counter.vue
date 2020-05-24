<template>
  <div>
    <div class="base-timer">
      <svg class="base-timer__svg" viewBox="0 0 100 100" xmlns="http://www.w3.org/2000/svg">
        <g class="base-timer__circle">
          <circle class="base-timer__path-elapsed" cx="50" cy="50" r="45" />
          <path
            id="base-timer-path-remaining"
            stroke-dasharray="283 283"
            class="base-timer__path-remaining"
            d="
          M 50, 50
          m -45, 0
          a 45,45 0 1,0 90,0
          a 45,45 0 1,0 -90,0
        "
          />
        </g>
      </svg>
      <span id="base-timer-label" class="base-timer__label">{{formatTimeLeft(timeLeft)}}</span>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      timeLeft: 20,
      timePassed: 0,
      maxTime: 20,
      COLOR_CODES: {
        info: {
          color: "green"
        }
      }
    };
  },
  computed: {
    timeLimit: {
      get() {
        return this.maxTime;
      }
    },
    remainingPathColor: function() {
      return this.COLOR_CODES.info.color;
    }
  },
  methods: {
    formatTimeLeft: function(time) {
      const minutes = Math.floor(time / 60);
      let seconds = time % 60;
      if (seconds < 10) {
        seconds = `0${seconds}`;
      }
      return `${minutes}:${seconds}`;
    },
    startTimer: function() {
      const id = setInterval(() => {
        this.timePassed = this.timePassed + 1;
        this.timeLeft = this.timeLimit - this.timePassed;
        if (this.timeLeft <= 0) {
          clearInterval(id);
        }
        if (this.timeLeft <= 0.2 * this.timeLimit) {
          document
            .getElementById("base-timer-path-remaining")
            .setAttribute("stroke", "red");
        } else if (this.timeLeft <= 0.5 * this.timeLimit) {
          document
            .getElementById("base-timer-path-remaining")
            .setAttribute("stroke", "goldenrod");
        } else {
          document
            .getElementById("base-timer-path-remaining")
            .setAttribute("stroke", "#41B883");
        }
        this.setCircleDasharray();
      }, 1000);
    },
    calculateTimeFraction: function() {
      const rawTimeFraction = this.timeLeft / this.timeLimit;
      return rawTimeFraction - (1 / this.timeLimit) * (1 - rawTimeFraction);
    },
    setCircleDasharray: function() {
      const circleDasharray = `${(this.calculateTimeFraction() * 283).toFixed(
        0
      )} 283`;
      document
        .getElementById("base-timer-path-remaining")
        .setAttribute("stroke-dasharray", circleDasharray);
    }
  },
  created() {
    this.startTimer();
  }
};
</script>

<style scoped>
.base-timer {
  position: relative;
  height: 300px;
  width: 300px;
}

.base-timer__circle {
  fill: none;
  stroke: none;
}

.base-timer__path-elapsed {
  stroke-width: 10px;
  stroke: currentColor;
}

.base-timer__label {
  position: absolute;
  width: 300px;
  height: 300px;
  top: 0;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 70px;
  font-weight: 800;
  
}
.base-timer__path-remaining {
  stroke-width: 10px;

  stroke-linecap: round;

  transform: rotate(90deg);
  transform-origin: center;

  transition: 1s linear all;
  
}

.base-timer__svg {
  transform: scaleX(-1);
}
</style>
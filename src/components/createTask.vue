<template>
  <div v-if='goneForever'>
    <addJob @click.native='jobAddfn' v-if='!jobAdded'></addJob>
    <div v-else class='containerCreate'>
      <div class='inputBoth'>
        <span class='inputBut'>$</span>
        <input type='text' autofocus v-model="inputText" placeholder="rake do_something" v-if='!submitted' class='inputBar'>
        <div class='inputBar' v-else style='text-align:left; display:flex;align-items:center'>{{ inputText }}</div>
      </div>
      <div class='borderBottom'></div>
      <div class='floatSection'>
        <div class='columns'>
          <div class='dyno'>
            <h6>DYNO SIZE</h6>
            <select v-model="dynoSize" v-if='!submitted' class='selectThing'>
              <option value='free' selected="selected">Free</option>
            </select>
            <div v-else>{{ dynoSize }}</div>
          </div>
        </div>
        <div class='columns'>
          <div class='dyno'>
            <h6>FREQUENCY</h6>
            <select v-model="frequency" v-if='!submitted' class='selectThing'>
              <option value='Daily' selected="selected">Daily</option>
              <option value='Hourly'>Hourly</option>
              <option value='Every 10 minutes'>Every 10 minutes</option>
            </select>
            <div v-else>{{ frequency }}</div>
          </div>
        </div>
        <div class='columns'>
          <div class='dyno'>
            <h6>LAST RUN</h6> never
          </div>
        </div>
        <div class='columns'>
          <div class='dyno'>
            <h6>NEXT DUE</h6>
            <span id='date'>{{ date }}</span>
            <select v-model="nextDue" v-if='!submitted'>
              <option value='-'>----</option>
              <option value='0' selected="selected">00:00</option>
              <option value='30'>00:30</option>
              <option value='60'>01:00</option>
              <option value='90'>01:30</option>
              <option value='120'>02:00</option>
              <option value='150'>02:30</option>
              <option value='180'>03:00</option>
              <option value='210'>03:30</option>
              <option value='240'>04:00</option>
              <option value='270'>04:30</option>
              <option value='300'>05:00</option>
              <option value='330'>05:30</option>
              <option value='360'>06:00</option>
              <option value='390'>06:30</option>
              <option value='420'>07:00</option>
              <option value='450'>07:30</option>
              <option value='480'>08:00</option>
              <option value='510'>08:30</option>
              <option value='540'>09:00</option>
              <option value='570'>09:30</option>
              <option value='600'>10:00</option>
              <option value='630'>10:30</option>
              <option value='660'>11:00</option>
              <option value='690'>11:30</option>
              <option value='720'>12:00</option>
              <option value='750'>12:30</option>
              <option value='780'>13:00</option>
              <option value='810'>13:30</option>
              <option value='840'>14:00</option>
              <option value='870'>14:30</option>
              <option value='900'>15:00</option>
              <option value='930'>15:30</option>
              <option value='960'>16:00</option>
              <option value='990'>16:30</option>
              <option value='1020'>17:00</option>
              <option value='1050'>17:30</option>
              <option value='1080'>18:00</option>
              <option value='1110'>18:30</option>
              <option value='1140'>19:00</option>
              <option value='1170'>19:30</option>
              <option value='1200'>20:00</option>
              <option value='1230'>20:30</option>
              <option value='1260'>21:00</option>
              <option value='1290'>21:30</option>
              <option value='1320'>22:00</option>
              <option value='1350'>22:30</option>
              <option value='1380'>23:00</option>
              <option value='1410'>23:30</option>
            </select> 
            <div v-else style='display: inline'>{{ nextDue }}</div> UTC
          </div>
        </div>
      </div>
      <div class='submitSection'>
        <input type="submit" v-if='!submitted' @click='submit' class="saveButton" value="Save">
        <input type="submit" v-else class="editButton" value="Edit" @click='back'>
        <a class='cancelButton' v-if='!submitted && !alreadySubmitted' @click="jobRemovefn">Cancel</a>
        <a class='cancelButton' v-else-if='alreadySubmitted' @click="cancel">Cancel</a>
        <a class='cancelButton' v-else @click='remove'>Remove</a>
        <Remove v-show='blackBackground'></Remove>
      </div>
    </div>
  </div>
</template>

<script>
  import Remove from './Remove';
  import addJob from './addJob';

  export default {
    name: 'createTask',
    data() {
      return {
        submitted: 0,
        alreadySubmitted: 0,
        jobAdded: 0,
        blackBackground: 0,
        goneForever: 1,
        date: '1',
        inputText: '',
        dynoSize: 'Free',
        frequency: 'Daily',
        nextDue: '00:00',
      };
    },
    components: {
      Remove,
      addJob,
    },
    methods: {
      submit() {
        if (!this.inputText) return;
        this.submitted = 1;
        // this.alreadySubmitted = 1;
      },
      // click() {
      //   console.log(this.$parent);
      //   // this.$parent.add = 1;
      // },
      cancel() {
        this.submitted = 1;
      },
      jobAddfn() {
        console.log('job add!');
        this.jobAdded = 1;
      },
      jobRemovefn() {
        console.log('job add!');
        this.jobAdded = 0;
      },
      back() {
        this.submitted = 0;
      },
      remove() {
        console.log('remove!');
        this.blackBackground = 1;
      },
      getToday() {
        const today = new Date();
        const month = [];
        month[0] = 'January';
        month[1] = 'February';
        month[2] = 'March';
        month[3] = 'April';
        month[4] = 'May';
        month[5] = 'June';
        month[6] = 'July';
        month[7] = 'August';
        month[8] = 'September';
        month[9] = 'October';
        month[10] = 'November';
        month[11] = 'December';
        const name = month[today.getMonth()];
        const date = `${name} ${today.getDate()}`;
        return date;
      },
    },
    created() {
      this.date = this.getToday();
    },
  };
</script>

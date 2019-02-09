<template>
  <v-layout column justify-center align-center>
    <v-flex xs12 sm8 md6>
      <v-card>
        <v-card-title class="headline font-weight-bold">Time Left Until Graduation!</v-card-title>
        <v-card-text justify-center>
           <countdown :time="gradDate" class="title" :interval="100">
             <template slot-scope="props">Time Remaining：{{ props.days }} days, {{ props.hours }} hours, {{ props.minutes }} minutes, {{ props.seconds }} seconds.</template>
</countdown>
       <v-progress-linear v-model="valueDeterminate"></v-progress-linear> {{ parseInt(this.valueDeterminate) }} %
<p class="text-md-center">
<i class="fas fa-skull fa-7x"></i>
&nbsp;
&nbsp;
&nbsp;
&nbsp;
<i class="fas fa-graduation-cap fa-7x"></i></p>

        </v-card-text>


        <v-card-actions>
          <v-spacer></v-spacer>
        </v-card-actions>
      </v-card>
    </v-flex>
  </v-layout>
</template>

<script>

let now = new Date()
let gradDate = new Date(2020, 11, 30)
let beginDate = new Date(2019, 0, 1)
let totalTime = gradDate - beginDate
let passedTime = now - beginDate
let remainingTime = gradDate - now

export default {
  data: function () {
    return {
      gradDate: remainingTime,
      valueDeterminate: passedTime * 100 / totalTime
    }
  }
}
</script>

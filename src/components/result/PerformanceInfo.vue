<template>
    <div>
        <v-layout d-flex wrap>
            <v-text-field hide-details outlined class="resultElement" readonly id="motor-class" :suffix="performance.classPercentage+'%'" label="Class" v-model="performance.motorDescription"></v-text-field>
            <v-text-field hide-details outlined class="resultElement" readonly id="thrust-time" label="Thrust time" suffix="s" v-model="performance.thrustTime"></v-text-field>
            <v-text-field hide-details outlined class="resultElement" readonly id="max-thrust" label="Max thrust" suffix="N" v-model="performance.maxThrust" ></v-text-field>
            <v-text-field hide-details outlined class="resultElement" readonly id="total-impulse" label="Total impulse" suffix="Ns" v-model="performance.totalImpulse"></v-text-field>
            <v-text-field hide-details outlined class="resultElement" readonly id="specific-impulse" label="Specific impulse" suffix="s" v-model="performance.specificImpulse"></v-text-field>
            <v-text-field hide-details outlined class="resultElement" readonly id="max-pressure" label="Max pressure" :suffix="units.resultPressureUnit" v-model="performance.maxPressure"></v-text-field>
            <v-text-field hide-details outlined class="resultElement" readonly id="average-pressure" label="Average pressure" :suffix="units.resultPressureUnit" v-model="performance.averagePressure"></v-text-field>
            <v-text-field hide-details outlined class="resultElement" readonly id="nozzle-exit-speed" label="Nozzle exit speed" prefix="Mach" v-model="performance.exitSpeedInitial"></v-text-field>
            <v-text-field hide-details outlined class="resultElement" readonly id="grain-mass" label="Initial grain mass" :suffix="units.massUnit" v-model="performance.grainMass"></v-text-field>
        </v-layout>
        <v-flex>
            <span class="label-nozzle" style="color: red;" v-if="performance.lowKNCorrection">
                Calculation performed in safe mode due to low KN or high (throat diam./core diam.) ratio.
                The result is approximate and the motor may be subject of chuffing.<br>
            </span>
            <span class="label-nozzle" style="color: orange;" v-if="performance.optimalDesign">Optimally designed nozzle with an expansion ratio of {{performance.optimalNozzleExpansionRatio}}</span>
        </v-flex>
    </div>

</template>

<script>
export default {
    name: 'PerformanceInfo',
    data() {
        return {
            performance: {}
        }
    },
    props: {
        units: Object
    }
}
</script>

<style lang="scss" scoped>
    .resultElement {
        width: 160px;
        margin: 0 10px;
        /*flex-grow: 0 !important;*/
        /*max-width: 250px;*/
        padding: 5px 0;
    }
</style>

<template>
    <div class="checkboxes-container">
        <h5>CheckBoxes</h5>
        <div class="checkbox-content" ref="container">
            <input type="checkbox" ref="inputCheckbox" :class="{'all-options-active' : isAllActive}" v-model="sport" v-for="(option, idx) in inputOptions" :key="idx" :value="option.value" :disabled="option.disabled" @change="tickCheckbox($event, options.value)" />
            <input type="checkbox" ref="resultCheckbox" @change="selectAll">
        </div>
    </div>
</template>
<script>
export default {
    name: 'eggplore-checkboxes',
    props: {
        options: {
            type: Array,
            validator: function (val) {
                if (val.length === 0) {
                    return true;
                }

                return val.find(item => typeof item == 'object')
            },
            default: () => []
        },
        value: {
            type: Array,
            default: () => []
        }
    },

    data(){
        return{
            isAllActive: false,
            sport: []
        }
    },
    computed: {
        inputOptions() {
            const options = JSON.parse(JSON.stringify(this.options));

            return options.map(item => {
                if (!item.disabled) {
                    item['disabled'] = false;
                }
                
                return item;
            })
        }
    },
    mounted() {
        this.init();
    },
    methods: {
        selectAll(){
            if(this.sport.length == 0){
                this.sport = this.options
                const input_elem = this.$refs.inputCheckbox
                input_elem.forEach(elem => {
                    if(elem.disabled){
                        // console.log(1,elem)
                    }else{
                        elem.classList.add('all-elem-active')
                        console.log(elem.classList)
                    }
                })
            }
            else{
                this.sport = []
                const input_elem = this.$refs.inputCheckbox
                input_elem.forEach(elem => {
                    if(elem.disabled){
                        // console.log(1,elem)
                    }else{
                        elem.classList.remove('all-elem-active')
                        elem.classList.remove('sport-active')
                        console.log(elem.classList)
                    }
                })
            }
        },
        
        init() {
            if (this.value.length > 0) {
                this.sport = this.value;
                const container = this.$refs.container;
                // console.log(typeof(container.childNodes))

                container.childNodes.forEach(el => {
                    // console.log(el.value)
                    if (this.sport.includes(el.value)) {
                        el.classList.add('sport-active')
                    }
                })

            }
        },
        tickCheckbox(e) {
            e.target.classList.toggle('sport-active')
        }
    },
    watch: {
        'sport': function (val) {
            const optionsCount = this.options.filter(item => !item.disabled).length;
            const inputCount = val.length;
            let resultcheck = this.$refs.resultCheckbox

            if (inputCount === 0) {
                resultcheck.classList.remove('checkbox-checked')
                resultcheck.classList.remove('checkbox-unchecked')
            } else if (inputCount < optionsCount) {
                resultcheck.classList.add('checkbox-unchecked')
                resultcheck.classList.remove('checkbox-checked')
            } else {
                resultcheck.classList.add('checkbox-checked')
                resultcheck.classList.remove('checkbox-unchecked')
            }
            this.$emit('change', val)
        }
    }
}
</script>
<template>
    <div class="container">
        <div class="row">
            <div class="col-xl-12 col-sm-8 col-sm-offset-2 col-md-6 col-md-offset-3">
                <h1 class="text-center">The supper Quize =))</h1>
            </div>
            <div class="col-xl-12 col-sm-8 col-sm-offset-2 col-md-6 col-md-offset-3">
                <transition name="flip" mode="out-in">
                    <component :is="mode" @answered="answered($event)" @confirmed="mode = 'app-question'"></component>
                </transition>
            </div>
        </div>
    </div>
</template>

<script type="text/babel">
    import Answer from "./components/Answer.vue";
    import Question from "./components/Question.vue";
    export default {
        name: 'app',
        data () {
            return {
                mode: 'app-question'
            }
        },
        methods: {
            answered(isCorect){
                if (isCorect) {
                    this.mode = 'app-answer';
                } else {
                    this.mode = 'app-question';
                    alert('wrong, try again');
                }
            }
        },
        components: {
            appQuestion: Question,
            appAnswer: Answer
        }
    }
</script>

<style>
    .flip-enter-active{
        animation:flip-in 0.5s ease-out forwards;
    }
    .flip-leave-active{
        animation:flip-out 0.5s ease-out forwards;
    }

    @keyframes flip-out{
        from{
            transform: rotateY(0deg);
        }
        to{
            transform: rotateY(90deg);
        }

    }
    @keyframes flip-in{
        from{
            transform: rotateY(90deg);

        }
        to{
            transform: rotateY(0deg);
        }

    }
</style>

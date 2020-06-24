<template>
    <div class="contact">
        <h1 class="headline">Your feedback is very important to us.</h1>
        <br/>
        <h3 class="text">If you have any issues whatsoever using our website, please feel free to use this contact form that is
            definitely connected to a back-end and will most certainly send your complaint to a human being, and not into the yawning void.</h3>
        <textarea class="contactTxtArea" id="field" placeholder="Go for it, champ."></textarea>
        <v-btn class="mx-2" fab dark small color="primary" @click="send">
            <v-icon dark>send</v-icon>
        </v-btn>
    </div>
</template>

<script>
    export default {
        name: "Contact",

        methods: {
            send() {
                document.getElementById("field").value = "Thanks for sending your feedback! We'll get right on that."
            }
        }
    }
</script>

<style scoped>
    .mx-2 {
        margin: 0;
        position: absolute;
        top: 77%;
        left: 90%;
        -ms-transform: translate(-50%, -50%);
        transform: translate(-50%, -50%);
    }

    .contactTxtArea {
        background-color: whitesmoke;
        height: 40%;
        width: 75%;
        margin: 0;
        position: absolute;
        top: 60%;
        left: 50%;
        -ms-transform: translate(-50%, -50%);
        transform: translate(-50%, -50%);
    }

    .headline {
        width: 75%;
        margin: 0;
        position: absolute;
        top: 10%;
        left: 50%;
        -ms-transform: translate(-50%, -50%);
        transform: translate(-50%, -50%);
    }

    .text {
        width: 75%;
        margin: 0;
        position: absolute;
        top: 25%;
        left: 50%;
        -ms-transform: translate(-50%, -50%);
        transform: translate(-50%, -50%);
    }

    .contact {
        background: #062a37;
        color: whitesmoke;
        width: 75%;
        height: 75%;
        margin: 0;
        position: absolute;
        top: 50%;
        left: 50%;
        -ms-transform: translate(-50%, -50%);
        transform: translate(-50%, -50%);
        /*padding: 3vh;*/
        border-left: 2px solid #c7d1e0;
        border-right: 2px solid #c7d1e0;
        border-bottom: 1px solid #c7d1e0;
        border-top: 1px solid #c7d1e0;
        border-radius:50px;
    }
</style>
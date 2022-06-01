<template>
    <div class="UserProfile">
        <div class="UserProfile_UserPanel">
            <h1 class="UserProfile_Username">@{{ user.username }} </h1>
            <div class="UserProfile_AdminBadge" v-if="user.isAdmin">
                Admin
            </div>
            <div class="UserProfile_FollowerCount">
                <strong>followers:
                </strong>{{ state.followers }}
            </div>
            <CreateTwootPanel @add-twoot="addTwoot" />

        </div>
        <div class="UserProfile_twoots_wrapper">
            <TwootItem :key="twoot.id" v-for="twoot in state.user.twoots" :username="state.user.username"
                :twoot="twoot" />

        </div>
    </div>
</template>

<script>
import { reactive } from "vue"
import TwootItem from './TwootItem.vue';
import CreateTwootPanel from './CreateTwootPanel.vue';
export default {
    components: { TwootItem, CreateTwootPanel },
    setup() {
        const state = reactive({
            followers: 0,
            user: {
                id: 1,
                username: "_Kratos87Orochi",
                firstName: "Kratos",
                lastName: "Orochi",
                email: "orichi@learnercolab.com",
                isAdmin: true,
                twoots: [
                    {
                        id: 1,
                        content: "Twooter is Amazing!"
                    },
                    {
                        id: 2,
                        content: "What is Gamora?"
                    }
                ]
            }
        });

        function addTwoot(twoot) {
            state.user.twoots.unshift({ id: state.user.twoots.length + 1, content: twoot });
        }
        return {
            state,
            addTwoot
        }
    }
}
</script>

<style lang="scss" scoped>
.UserProfile {
    height: 15rem;
    margin-top: 5%;
    display: flex;
    flex-direction: column;
    padding: 2% 1%;

    .UserProfile_UserPanel {
        background-color: white;
        margin: 0 auto;
        border-radius: 6px;
        height: fit-content;
        width: 70%;
        padding: 1%;
        box-shadow: rgba(60, 64, 67, 0.3) 0px 1px 2px 0px, rgba(60, 64, 67, 0.15) 0px 1px 3px 1px;

        h1 {
            margin: 0;
        }

        .UserProfile_AdminBadge,
        .UserProfile_NotAdmin {
            color: white;
            padding: 1%;
            background-color: #68E1FB;
            width: 40%;
            font-weight: 700;
            border-radius: 6px;
            margin: 0 auto;
            margin-bottom: 4%;

        }



        .UserProfile_twoots_wrapper {
            margin: 0 auto;
            margin-top: 2.2%;
            width: 35%;
        }
    }

}
</style>
<template>
    <div :class="$root.isMobile ? 'my-4' : 'mb-6'" class="is-flex is-justify-content-center">
        <h1 :class="$root.isMobile ? 'is-size-6' : 'is-size-5'">Let's keep this short and simple</h1>
    </div>
    <div class="container is-widescreen" :style="$root.isMobile ? '' : 'padding-bottom: 10rem;'">
        <div class="columns is-clipped">
            <div class="column is-flex is-align-items-center is-justify-content-flex-end">
                <div :class="$root.isMobile ? '' : 'stats-margin'" class="is-relative" style="width: min(600px, 100%);">
                    <div class="mt-4 tile is-ancestor is-vertical">
                        <div :class="$root.isMobile ? 'is-hidden' : 'is-flex'">
                            <div class="tile"></div>
                            <div class="tile"></div>
                            <div class="tile is-vertical is-parent">
                                <div class="tile is-child box has-background-light-black">
                                </div>
                                <div class="tile is-child box has-background-light-black">
                                </div>
                            </div>
                        </div>
                        <div class="is-flex">
                            <div :class="$root.isMobile ? 'is-hidden' : 'tile'"></div>
                            <div class="tile bottom-stats is-vertical is-parent">
                                <div class="tile is-child box has-background-primary">
                                    <p class="has-text-white has-text-right">{{`I'm ${Math.floor((new Date()-new Date("November 18, 2006 00:00:00"))/1000/3600/24/365)} years old.`}}</p>
                                </div>
                            </div>
                        </div>
                        <div class="is-flex">
                            <div :style="$root.isMobile ? 'display:none;' : 'width:25%'"></div>
                            <div class="tile bottom-stats is-vertical is-parent">
                                <div class="tile is-child box has-background-primary">
                                    <p class="has-text-white has-text-right">Located in Toronto, Ontario</p>
                                </div>
                            </div>
                        </div>
                        <div class="is-flex">
                            <div class="tile name-stats is-parent">
                                <div class="tile is-child box has-background-primary">
                                    <p class="has-text-white mb-2 my-name title has-text-right">Daniel Morgan</p>
                                    <p class="has-text-white my-job has-text-right">Web & Game Developer</p>
                                </div>
                            </div>
                        </div>
                        <div class="is-flex">
                            <div :class="$root.isMobile ? 'is-hidden' : 'tile'"></div>
                            <div class="tile bottom-stats is-vertical is-parent">
                                <div class="tile is-child box has-background-primary is-justify-content-flex-end is-flex">
                                    <a class="about-icon" href="https://discord.com/users/480514992618078228"><img src="https://img.icons8.com/ios-filled/30/000000/discord-logo.png"/></a>
                                    <a class="about-icon" href="mailto:me@danielmorgan.xyz"><img src="https://img.icons8.com/ios-glyphs/30/000000/new-post.png"/></a>
                                    <a class="about-icon" href="https://github.com/dmrgn"><img src="https://img.icons8.com/ios-glyphs/30/000000/github.png"/></a>
                                </div>
                            </div>
                        </div>
                        <div :class="$root.isMobile ? 'is-hidden' : 'is-flex'">
                            <div class="tile"></div>
                            <div class="tile"></div>
                            <div class="tile is-vertical is-parent">
                                <div class="tile is-child box has-background-light-black">
                                </div>
                                <div class="tile is-child box has-background-light-black">
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
            <div class="column is-relative is-flex is-align-items-center">
                <!-- <div class="band"></div> -->
                <div style="width: 100%" class="card box has-background-light-black">
                    <div class="card-content has-background-light-black">
                        <div class="media mb-4">
                            <div class="media-left">
                                <figure class="image is-64x64">
                                    <img class="is-rounded" :src="`https://cdn.discordapp.com/avatars/480514992618078228/${discordData?.discord_user?.avatar}.webp?size=64`" alt="Placeholder image">
                                </figure>
                            </div>
                            <div class="media-content">
                                <p class="title is-4 mb-0 has-text-white">Daniel Morgan</p>
                                <div class="link">
                                    <a :href="`https://discord.com/users/${discordData?.discord_user?.id}`" class="subtitle has-text-secondary is-6">{{discordData?.discord_user?.username + "#" + discordData?.discord_user?.discriminator}}</a>
                                </div>
                            </div>
                        </div>
                        <div v-if="discordData?.discord_status == 'offline'">
                            <p class="">hmmm... looks like I'm offline!</p>
                        </div>
                        <div v-if="discordData?.activities?.[0]?.id == 'custom'">
                            <p class="has-text-white">{{`"${discordData?.activities?.[0]?.state}"`}}</p>
                            <div v-if="discordData?.activities?.length > 1" class="mb-4"></div>
                        </div>
                        <div v-if="(discordData?.activities?.length == 1 && discordData?.activities?.[0]?.id != 'custom') || discordData?.activities?.length > 1">   
                            <p class="has-text-weight-bold">Looks like I'm currently working with:</p>
                        </div>
                        <div v-for="(activity, index) in discordData?.activities" :key="index">
                            <div v-if="index > 0" class="pt-4"></div>
                            <div v-if="activity?.id != 'custom' && activity?.state">
                                <div class="media has-background-light-black">
                                    <div v-if="activity?.assets?.large_image && activity?.application_id" class="media-left">
                                        <figure class="image is-48x48">
                                            <img class="is-rounded" :src="`https://cdn.discordapp.com/app-assets/${activity?.application_id}/${activity?.assets?.large_image}.png`" alt="Placeholder image">
                                        </figure>
                                    </div>
                                    <div class="mr-4" v-if="activity.name == 'Spotify'">
                                        <figure class="image is-48x48">
                                            <img class="album-image" :src="`https://i.scdn.co/image/${this.discordData.activities[index].assets.large_image.split(':')[1]}`" alt="Placeholder image">
                                        </figure>
                                    </div>
                                    <div class="media-content">
                                        <p class="is-4 has-text-white">{{activity?.name}}</p>
                                        <span class="subtitle is-6 is-flex">
                                            {{activity?.state + ((activity?.details) ? ": " + activity?.details : '')}}
                                        </span>
                                    </div>
                                </div>
                            </div>
                        </div>
                    </div>
                    <div class="ml-5 mb-2">
                        <time style="margin-bottom: -1rem; font-size: 14px; font-weight: bold" class="has-text-grey is-uppercase" :datetime="dateTimeString">{{currentTime}}</time>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
    const DISCORD_ID = `480514992618078228`;
    import moment from "moment";
    export default {
        name:"AboutSection",
        data() {
            return {
                discordData: null,
                currentTime: null,
                dateTimeString: null
            }
        },
        async mounted () {
            this.discordData = (await
                (await fetch(`https://api.lanyard.rest/v1/users/${DISCORD_ID}`)).json()
            ).data;
            console.log(this.discordData.activities);
            setInterval(() => {
                const est = moment.utc().subtract(4,"hour");
                this.currentTime = `${est.format('MMMM Do YYYY, h:mm:ss a')} EST`;
                this.dateTimeString = `${est.year()}-${est.month()}-${est.day()}`;
            }, 1000)
        },
    }
</script>

<style lang="scss" scoped>
    @import "../../assets/main.scss";
    .has-text-grey {
        color: rgb(74,74,74) !important;
    }
    .has-background-light-black {
        background-color: lighten($black, 5%);
    }
    .band {
        position: absolute;
        background-color: $secondary;
        width: 33%;
        height: 100%;
        left: 33%;
        border-radius: 6px;
    }
    .band::before {
        content: "";
        position: absolute;
        background-color: $secondary;
        width: 33%;
        height: 80%;
        top: 10%;
        left: -60%;
        border-radius: 6px;
    }
    .band::after {
        content: "";
        position: absolute;
        background-color: $secondary;
        width: 33%;
        height: 80%;
        top: 10%;
        right: -60%;
        border-radius: 6px;
    }
    .stats-margin {
        margin-right: calc(4rem + 12px);
    }
    .top-stats {
        width: 400px;
    }
    .my-name {
        font-size: 3rem;
    }
    .about-icon {
        @extend .mx-3;
        filter: invert(100);
        transition: all 0.5s;
        transform: scale(1, 1);
        display: flex;
        align-items: center;
    }
    .about-icon:hover {
        transform: scale(1.5, 1.5);
    }
    .link {
        transform: scale(1, 1);
        transition: all 1s;
        position: relative;
        left: -50%;
    }
    .link > a {
        position: relative;
        left: 50%;
    }
    .link:hover {
        transform: scale(1.2, 1.2);
    }
    a {
        color: $primary;
    }
    .album-image {
        border-radius: 6px;
    }
</style>
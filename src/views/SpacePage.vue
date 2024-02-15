
<template>
    <div class="space-page">
        <h1 class="space-page__title">
            Space
        </h1>
        <div class="highlight-container">
            <MuseumHighlight v-for="highlight in spaceHighlights" colour="white" :highlight="highlight">
                <template v-slot:corner-icon>
                    <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="currentColor" class="icon">
                        <path fill-rule="evenodd"
                            d="M10.788 3.21c.448-1.077 1.976-1.077 2.424 0l2.082 5.006 5.404.434c1.164.093 1.636 1.545.749 2.305l-4.117 3.527 1.257 5.273c.271 1.136-.964 2.033-1.96 1.425L12 18.354 7.373 21.18c-.996.608-2.231-.29-1.96-1.425l1.257-5.273-4.117-3.527c-.887-.76-.415-2.212.749-2.305l5.404-.434 2.082-5.005Z"
                            clip-rule="evenodd" />
                    </svg>
                </template>
                <template v-slot:description>
                    <div v-if="highlight.description" class="card-description" :title="highlight?.description">
                        {{ highlight?.description }}
                    </div>
                    <div v-if="highlight.info" class="card-description" :title="highlight?.info">
                        {{ highlight.info }}
                    </div>
                    <div v-if="highlight?.news?.title" class="card-description" style="margin-top:10px;">
                        {{ highlight.news.title }} <span v-if="highlight?.news?.date">at {{ highlight.news.date }}</span>
                    </div>
                    <div v-if="highlight?.quiz" class="card-description" style="margin-top:10px;">
                        <a :href="highlight.quiz">Try our planet questionnaire!</a>
                    </div>
                </template>
            </MuseumHighlight>
            <MuseumHighlight colour="#ADD8E6" :highlight="spacePartners.observatory">
                <template v-slot:corner-icon>
                    <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="currentColor" class="icon">
                        <path fill-rule="evenodd"
                            d="M10.788 3.21c.448-1.077 1.976-1.077 2.424 0l2.082 5.006 5.404.434c1.164.093 1.636 1.545.749 2.305l-4.117 3.527 1.257 5.273c.271 1.136-.964 2.033-1.96 1.425L12 18.354 7.373 21.18c-.996.608-2.231-.29-1.96-1.425l1.257-5.273-4.117-3.527c-.887-.76-.415-2.212.749-2.305l5.404-.434 2.082-5.005Z"
                            clip-rule="evenodd" />
                    </svg>
                </template>
                <template v-slot:description>
                    <div class="card-description" :title="highlight?.description">
                        {{ spacePartners.observatory?.info }}
                    </div>
                </template>
            </MuseumHighlight>
        </div>
    </div>
</template>
<script>

import MuseumHighlight from '../components/MuseumHighlight.vue';

export default {
    name: 'SpacePage',
    components: {
        MuseumHighlight,
    },
    data() {
        return {
            spaceHighlights: [
                {
                    date: '2020-04-20 12:20:00',
                    description: 'Asteroids are minor planets, especially of the inner Solar System. Larger asteroids have also been called planetoids.',
                    id: 1,
                    image: 'asteroid.png',
                    name: 'Asteroids',
                },
                {
                    date: '2020-05-20 15:50:00',
                    description: 'A comet is an icy, small Solar System body that, when passing close to the Sun, warms and begins to release gases, a process called outgassing.',
                    id: 9,
                    image: 'comet.jpg',
                    name: 'Comets',
                },
                {
                    date: '2020-05-01 9:22:00',
                    description: 'The term planet is ancient, with ties to history, astrology, science, mythology, and religion.',
                    id: 7,
                    image: 'planet.jpg',
                    name: 'Planets',
                    news: {
                        date: '2020-08-18 18:00:00',
                        title: 'Attend our talk about Jupiter with Dr. Hogarth',
                    },
                    quiz: 'https://planetquiz.space',
                },
                {
                    date: '2020-07-05 4:10:00',
                    description: 'A meteor shower is a celestial event in which a number of meteors are observed to radiate, or originate, from one point in the night sky.',
                    id: 12,
                    image: 'meteor.jpg',
                    name: 'Meteor showers',
                    news: {
                        title: 'The Lyrids will peak at on April 21-22 2021, at night',
                    },
                },
            ],
            spacePartners: {
                observatory: {
                    createdAt: '2020-06-01 11:45:00',
                    info: 'The Mauna Kea Observatories (MKO) are a number of independent astronomical research facilities and large telescope observatories that are located at the summit of Mauna Kea on the Big Island of Hawaiʻi, United States.',
                    image: 'observatory.png',
                    name: 'Mauna Kea Observatories',
                },
            },
        };
    },
    mounted() {
        this.spaceHighlights.sort((a, b) => new Date(a.date) - new Date(b.date));
    },
};
</script>

<style lang="scss" scoped>
.space-page {
    margin: 60px;
}

.space-page__title {
    margin-bottom: 24px;
}

.highlight-container {
    display: flex;
    flex-wrap: wrap;
    gap: 2rem;
}

.icon {
    width: 3rem;
    height: 3rem;
}
</style>

<template>
    <div class="museum-highlight">
        <div class="card" :style="{ backgroundColor: colour }">
            <div class="text-container">
                <slot name="corner-icon"></slot>
            </div>
            <a href="#">
                <img class="card-img" :src="'/img/' + highlight?.image" :alt="highlight?.name" />
            </a>
            <div class="card-body">
                <h5 class="card-label">{{ highlight?.name }} </h5>
                <h6>{{ highlight?.date }}</h6>
                <slot name="description"></slot>
            </div>
        </div>
        <div class="justify-center">
            <a @click="refreshImage()" class="card-action-btn">Refresh Image
            </a>
        </div>
    </div>
</template>

<script>
export default {
    name: 'MuseumHighlight',
    props: {
        highlight: {
            type: Object,
            required: true,
        },
        colour: {
            type: String,
            required: false,
            default: '#FFFFFF'
        }
    },
    methods: {
        refreshImage() {
            let images = ["asteroid.png", "comet.jpg", "meteor.jpg", "observatory.png", "planet.jpg"];
            images.splice(images.indexOf(this.highlight.image), 1);
            const randomImage = images[Math.floor(Math.random() * images.length)];
            this.highlight.image = randomImage;
        },
    },
};
</script>

<style lang="scss" scoped>
.space-page {
    &__title {
        color: #2c3791;
        font-size: 24px;
        font-weight: 600;
    }

    .card {
        position: relative;
        border-radius: 0.5rem;
        border-width: 1px;
        border-color: #E5E7EB;
        max-width: 24rem;
        background-color: #ffffff;
        box-shadow: 0 1px 3px 0 rgba(0, 0, 0, 0.1), 0 1px 2px 0 rgba(0, 0, 0, 0.06);
        height: 550px;
        width: 400px;
    }

    .card-img {
        padding: 1rem;
        width: 100%;
        border-radius: 50px;
    }

    .card-body {
        padding-left: 1.25rem;
        padding-right: 1.25rem;
        padding-bottom: 1.25rem;
        height: 150px;
        overflow:auto;
    }
    .card-label {
        font-size: 1.25rem;
        line-height: 1.75rem;
        font-weight: 600;
        letter-spacing: -0.025em;
        color: #111827;
    }

    .justify-center {
        display: flex;
        justify-content: center;
    }

    .card-action-btn {
        padding-top: 0.625rem;
        padding-bottom: 0.625rem;
        padding-left: 1.25rem;
        padding-right: 1.25rem;
        border-radius: 0.5rem;
        font-size: 0.875rem;
        line-height: 1.25rem;
        font-weight: 500;
        text-align: center;
        color: #ffffff;
        background-color: #1D4ED8;
        cursor: pointer;
        margin-top: 20px;
    }

    .card-action-btn:hover {
        background-color: #1E40AF;
    }
    .text-container {
        position: absolute;
        top: -20px;
        right: -20px;
    }
}
</style>

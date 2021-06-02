<template>
    <section class="points">
        <div class="points__players">
            <span class="points__player">{{ kaiser.name }}</span>
            <span class="points__player">{{ notKaiser.name }}</span>
        </div>
        <div class="points__scores">
            <span class="points__score">{{ kaiser.scores }}</span>
            <span class="points__score">{{ notKaiser.scores }}</span>
        </div>
        <div class="points__scores-total">
            <span class="points__total">Всего: {{ kaiser.scoresTotal }}</span>
            <span class="points__total">Всего: {{ notKaiser.scoresTotal }}</span>
        </div>
    </section>
</template>

<script>
import { kaiser, notKaiser } from '@/data.js';

export default {
    name: 'Points',
    data() {
        return {
            kaiser,
            notKaiser,
        };
    },
};
</script>

<style>
.points {
    width: 80%;
    display: flex;
    flex-direction: column;
    align-items: center;
    box-shadow: #a8a8a8 0 0 10px 3px;
    border-radius: 25px;
    padding: 40px;
}

.points__players,
.points__scores,
.points__scores-total {
    display: flex;
    justify-content: space-around;
    width: 100%;
    margin-bottom: 40px;
}

.points__scores-total {
    border-top: #a8a8a8 1px solid;
    padding-top: 40px;
    margin-bottom: 0;
}

.points__player {
    font-weight: 700;
    font-size: 34px;
    line-height: 1.2;
    width: 50%;
}

.points__player:first-of-type {
    border-right: 1px solid;
}

.points__score {
    font-weight: 900;
    font-size: 150px;
    line-height: 1.2;
}

@media screen and (max-width: 767px) {
    .points {
        padding: 20px;
    }

    .points__players,
    .points__scores-total {
        margin-bottom: 20px;
    }

    .points__scores {
        margin-bottom: 0;
    }

    .points__player {
        font-size: 22px;
    }
}
</style>
<template>
    <section class="points">
        <div class="points__players">
            <span class="points__player">{{ kaiser.name }}</span>
            <span class="points__player">{{ notKaiser.name }}</span>
        </div>
        <div class="points__scores">
            <div class="points__score-container">
                <span class="points__score points__score_kaiser">{{ kaiser.scores }}</span>
            </div>
            <div class="points__score-container">
                <span class="points__score points__score_not-kaiser">{{ notKaiser.scores }}</span>
            </div>
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
    mounted() {
        const kaiser = document.querySelector('.points__score_kaiser');
        const notKaiser = document.querySelector('.points__score_not-kaiser');

        const kaiserScores = kaiser.textContent;
        const notKaiserScores = notKaiser.textContent;

        if (kaiserScores > notKaiserScores) {
            kaiser.classList.add('winner');
            notKaiser.classList.add('looser');
        } else if (kaiserScores < notKaiserScores) {
            kaiser.classList.add('looser');
            notKaiser.classList.add('winner');
        } else {
            kaiser.classList.add('balance');
            notKaiser.classList.add('balance');
        }
    },
};
</script>

<style>
@keyframes scores-animation {
    from,
    to {
        transform: scale(1.0);
    }
    50% {
        transform: scale(5);
    }
}

@keyframes winner-animation {
    50% {
        color: green;
    }
}

@keyframes looser-animation {
    50% {
        color: red;
    }
}

@keyframes balance-animation {
    50% {
        color: yellow;
    }
}

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

.points__score-container {
    animation: scores-animation 3s ease-in-out 5s;
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

.winner {
    animation: winner-animation 3s ease-in-out 5s;
}
.looser {
    animation: looser-animation 3s ease-in-out 5s;
}
.balance {
    animation: balance-animation 3s ease-in-out 5s;
}
</style>

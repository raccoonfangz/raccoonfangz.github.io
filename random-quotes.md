---
layout: default
title: "Random quotes"
permalink: /random-quotes/
---

<style>
/* Hide upvotes completely (button + text) */
.upvote-button,
.upvote-count,
.upvote-button::after {
    display: none !important;
}

#quote {
    text-align: center;
    font-size: 1.5rem;
    margin-top: 55px;
    margin-bottom: 35px;
}
</style>

<p id="quote"></p>

<script>
  const quotes = [
    "I always wonder why birds stay in the same place when they can fly anywhere on the earth. Then I ask myself the same question. - Harun Yahya",
    "Wrong is wrong even if everyone is doing it. Right is right even if no one is doing it. - Saint Augustine",
    "When you arise in the morning, think of what a privilege it is to be alive, to think, to enjoy, to love. - Marcus Aurelius",
    "The best way to find yourself is to lose yourself in the service of others. - Mahatma Gandhi",
    "A friend to all is a friend to none. - Aristotle",
    "Men exist for the sake of one another. Teach them or bear with them. - Marcus Aurelius",
    "We become what we think about. - Earl Nightingale",
    "Hell is the absence of the people you long for. - Neil Gaiman",
    "The struggle itself towards the heights is enough to fill a man's heart. One must imagine Sisyphus happy. - Albert Camus",
    "What we do for ourselves dies with us. What we do for others and the world remains and is immortal. - Albert Pine",
    "Some people only 'wake up' when faced with a terminal illness... Time is passing, and so is your life. Start living now. - Ashton",
    "Dum spiro, spero (While I breathe, I hope) - Latin phrase",
    "Grief is just love that has nowhere to go. - Jamie Anderson",
    "The only way to have a friend is to be one. - Ralph Waldo Emerson",
    "We are no longer able to change a situation, we are challenged to change ourselves. - Viktor E. Frankl",
    "And once the storm is over, you won't remember how you made it through... That's what this storm's all about. - Haruki Murakami",
    "Ichi-go ichi-e (One time, one meeting)",
    "Only when we realise that it’s not another day, but one day less, we will begin to appreciate the truly important things. - Unknown",
    "The mystery of human existence lies not in just staying alive, but in finding something to live for. - Fyodor Dostoyevsky",
    "The fears we don’t face become our limits. - Robin Sharma",
    "Friendship is not about whom you have known the longest, but about who came and never left your side. - Unknown",
    "The man who moves a mountain begins by carrying away small stones. - Confucius",
    "Do not regret the love you gave. Even if it wasn’t returned, it was a reflection of who you are. - Unknown",
    "A mistake that humbles you is better than the achievement that makes you arrogant. - Unknown",
    "Better to have loved and lost than never loved at all. - Alfred Lord Tennyson",
    "Yesterday I was clever and I wanted to change the world, but today I am wise and I want to change myself. - Rumi",
    "You can’t change people around you but you can change people around you. - The Minimalists",
    "The more you sweat in the practice, the less you bleed in the battle. - Army proverb",
    "To be loved is to be changed. - Madeleine L’Engle",
    "The man who asks a question is a fool for a minute, the man who does not ask is a fool for life. - Confucius",
    "Different paths same sky. - Unknown",
    "World is cruel therefore I won’t be. - Unknown",
    "Not every day is good but there is something good in every day. - Unknown",
    "A tree falls the way it leans. - Unknown",
    "Only time can answer your questions. - Unknown",
    "To be angry is to let others' mistakes control you. To forgive is to control yourself. - Unknown",
    "As long as you have yourself, you have someone. - Unknown",
    "Don’t strive to be well known, strive to be worth knowing. - Unknown",
    "You can either complain about your problems, or change them. - Unknown",
    "A person who makes you chase isn’t worth chasing. - Unknown",
    "No reason to stay is a good reason to leave. - Unknown"
  ];

  document.getElementById("quote").textContent = quotes[Math.floor(Math.random() * quotes.length)];
</script>

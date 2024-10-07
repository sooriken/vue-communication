<template>
    <header>
        <nav>
            <a href="#">Правила</a>
            <a href="#">Игра</a>
            <a href="#">Faq</a>
        </nav>
    </header>
</template>


<style>
    header {
        padding: 20px;
        background-color: rgba(153, 153, 255, 0.5);;
    }
    nav {
        display: flex;
        justify-content: space-around;
    }
    a {
        text-decoration: none;
        color: #330066;
        cursor: pointer;
    }
    a:hover {
        text-decoration: underline;
    }
</style>
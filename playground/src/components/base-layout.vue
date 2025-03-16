<template>
    <div class="wrapper">
        <aside class="sidebar">
            <slot name="sidebar" />
        </aside>
        <main class="main">
            <slot name="main" />
        </main>
    </div>
    <footer class="footer">
        <slot name="footer" />
    </footer>
</template>
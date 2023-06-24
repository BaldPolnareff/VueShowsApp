<template>
    <div class="header">
        <slot name="header"></slot>
    </div>
    <div class="body">
        <h1>Title</h1>
        <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Optio tenetur, aspernatur labore aliquam fuga ad?</p>
        <slot></slot>
    </div>
    <div class="footer">
        <slot name="footer"></slot>
    </div>
</template>
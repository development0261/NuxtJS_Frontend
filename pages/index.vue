<template>
<div class="cursor-inner">
  <div id="cur" class="cursor" @mousemove="move()">
    <div class="container">
      <div class="title-wrap">
        <h1 class="title" @mouseenter="enter()" @mouseout="out()">Welcome</h1>
      </div>
      <div class="videoContainer">
        <video width="640" height="" class="demodemo"  controls loop muted autoplay oncanplay="this.play()" onloadedmetadata="this.muted = true">
          <source src="../assets/demo1.mp4?autoplay=1" type="video/mp4">
        </video>
      </div>
    </div>

  </div>
</div>
</template>

<script>

export default {
  methods: {
    move() {
      var h =document.querySelector('.cursor');

      document.body.onmousemove = function(e) {
        h.style.setProperty('background-position',(e.clientX - 15)+'px '+(e.clientY - 15)+'px');
      }
    },
    enter() {
      var title =document.querySelector('.title');
      title.classList.add("title-enter");
    },
    out() {
      var title = document.querySelector('.title');
      title.classList.add("title");
      title.classList.remove("title-enter");
    }
  }
  
}
</script>

<style>
.container {
  margin: 0 auto;
  min-height: 100vh;
  display: block;
  justify-content: center;
  align-items: center;
  text-align: center;
  width: 100%;
}
#cur.cursor {
  color: #fff;
  position: relative;
  background:
    radial-gradient(farthest-side, 
     transparent calc(100% - 3px),
     #000 calc(100% - 2px) calc(100% - 1px),
     transparent 100%) 
     fixed
     no-repeat;
  background-size:70px 70px;
}
.cursor-inner {
  background-image: url(https://images.unsplash.com/photo-1519750783826-e2420f4d687f?ixlib=rb-1.2.1&ixid=MXwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHw%3D&auto=format&fit=crop&w=1534&q=80);
      background-size: cover;
    background-repeat: no-repeat;
    background-position: center center !important;
    position: relative;
}

.title {
    color: #fff;
    padding-top: 30px;
    transition: all 0.3s ease 0s;
    margin-bottom: 60px;
    display: inline-block;
}
.title-wrap {
  text-align: center;
}
.title-enter {
    color: transparent;
    transition: all 0.3s ease 0s;
    -webkit-text-fill-color: transparent;
    -webkit-text-stroke-width: 1px;
    -webkit-text-stroke-color: white;
}
.cursor-inner:before {
  content: "";
  position: absolute;
  right: 0;
  left: 0;
  bottom: 0;
  top: 0;
  background: rgb(255 255 255 / 22%);
}
</style>

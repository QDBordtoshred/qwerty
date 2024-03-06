---
layout: default
title: Student Blog
---


## Build you Home Page here 
This is about your journey. Start now!!!

## Overview of Hacks, Study and Tangibles
Blogging in GitHub pages is a way to learn and code at the same time. 

- Plans, Lists, [Scrum Boards](https://clickup.com/blog/scrum-board/) help you to track key events, show progress and record time.  Effort is a big part of your class grade.  Show plans and time spent!
- [Hacks(Todo)](https://levelup.gitconnected.com/six-ultimate-daily-hacks-for-every-programmer-60f5f10feae) enable you to stay in focus with key requirements of the class.  Each Hack will produce Tangibles.
- Tangibles or [Tangible Artifacts](https://en.wikipedia.org/wiki/Artifact_(software_development)) are things you accumulate as a learner and coder. 

<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Stickman Game</title>
  <style>
    body {
      margin: 0;
      overflow: hidden;
    }
#stickman {
      width: 50px;
      height: 100px;
      background-color: black;
      position: absolute;
      bottom: 0;
      left: 50%;
      transform: translateX(-50%);
    }
  </style>
</head>
<body>

<div id="stickman"></div>

<script>
  const stickman = document.getElementById("stickman");
  let positionX = window.innerWidth / 2 - 25; // Initial X position
  let positionY = 0; // Initial Y position
  let isJumping = false;

  function updateStickman() {
    stickman.style.left = positionX + "px";
    stickman.style.bottom = positionY + "px";
  }

  function jump() {
    if (!isJumping) {
      isJumping = true;
      let jumpHeight = 100;
      const jumpInterval = setInterval(() => {
        positionY += 5;
        jumpHeight -= 5;
        if (jumpHeight <= 0) {
          clearInterval(jumpInterval);
          isJumping = false;
        }
        updateStickman();
      }, 20);
    }
  }

  window.addEventListener("keydown", (event) => {
    if (event.key === "ArrowRight") {
      positionX += 10;
    } else if (event.key === "ArrowLeft") {
      positionX -= 10;
    } else if (event.key === "ArrowUp") {
      jump();
    }

    updateStickman();
  });
</script>

</body>
</html>


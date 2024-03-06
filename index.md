---
layout: default
title: Student Blog
---

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

    #line {
      width: 300px;
      height: 5px;
      background-color: green;
      position: absolute;
      bottom: 100px;
      left: 50%;
      transform: translateX(-50%);
    }
  </style>
</head>
<body>

<div id="stickman"></div>
<div id="line"></div>

<script>
  const stickman = document.getElementById("stickman");
  const line = document.getElementById("line");
  let positionX = window.innerWidth / 2 - 25; // Initial X position
  let positionY = 0; // Initial Y position
  let isJumping = false;
  let jumpHeight = 0;

  function updateStickman() {
    stickman.style.left = positionX + "px";
    stickman.style.bottom = positionY + "px";
  }

  function jump() {
    if (!isJumping) {
      isJumping = true;
      const jumpInterval = setInterval(() => {
        if (jumpHeight < 50) {
          // Jump up
          positionY += 5;
          jumpHeight += 5;
        } else if (jumpHeight >= 50 && jumpHeight < 100) {
          // Fall down
          positionY -= 5;
          jumpHeight += 5;
        } else {
          // Jump complete
          clearInterval(jumpInterval);
          isJumping = false;
          jumpHeight = 0;
        }
        updateStickman();
      }, 20);
    }
  }

  // Event listener for movement controls
  window.addEventListener("keydown", (event) => {
    if (event.key === "ArrowRight" && positionX < window.innerWidth - 50) {
      positionX += 10;
    } else if (event.key === "ArrowLeft" && positionX > 0) {
      positionX -= 10;
    } else if (event.key === "ArrowUp") {
      jump();
    }

    updateStickman();
  });

  updateStickman();
</script>

</body>
</html>

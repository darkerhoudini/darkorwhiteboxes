# darkorwhiteboxes
<html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Black and White Grid</title>
  <style>
    body, html {
      margin: 0;
      padding: 0;
      overflow: hidden;
      background-color: white;
    }
    .grid-container {
      display: grid;
      grid-template-columns: repeat(auto-fill, 100cm);
      grid-template-rows: repeat(auto-fill, 100cm);
      width: 100vw;
      height: 100vh;
    }
    .box {
      width: 100cm;
      height: 100cm;
      background-color: white;
      border: 1px solid #e0e0e0;
    }
    .box.black {
      background-color: black;
    }
  </style>
</head>
<body>

<div id="grid-container" class="grid-container"></div>

<script>
  document.addEventListener("DOMContentLoaded", function () {
    const container = document.getElementById("grid-container");
    const totalBoxes = Math.ceil(window.innerWidth / 37.795) * Math.ceil(window.innerHeight / 37.795);
    let clickedBoxes = 0;

    for (let i = 0; i < totalBoxes; i++) {
      const box = document.createElement("div");
      box.classList.add("box");
      box.addEventListener("click", function () {
        if (!box.classList.contains("black")) {
          box.classList.add("black");
          clickedBoxes++;
        }

        if (clickedBoxes === totalBoxes) {
          setTimeout(reverseGrid, 500);
        }
      });
      container.appendChild(box);
    }

    function reverseGrid() {
      const boxes = document.querySelectorAll(".box");
      boxes.forEach((box) => {
        box.classList.remove("black");
      });
      clickedBoxes = 0;
    }

    window.addEventListener("resize", () => location.reload());
  });
</script>

</body>
</html>

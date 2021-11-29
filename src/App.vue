<template>
    <canvas id="myCanvas" width="1000" height="1000"></canvas>
</template>

<script>
addEventListener('click', createBox);
 let numberOfDots = 0;
  let pointA = {left:0,top:0};
  let pointB = {left:0,top:0};
  let firstPoint = {left:0,top:0};
function createBox(event) {
  ++numberOfDots;
  let box = document.createElement('div');
  box.className = 'box';
  box.style.left = event.pageX + 'px';
  box.style.top = event.pageY + 'px';
  if(!pointA.left && !pointA.top) {
    pointA.left = event.pageX; 
    pointA.top = event.pageY
  } else {
    pointB.left = event.pageX; 
    pointB.top = event.pageY
  }
  console.log(pointA,pointB)
  
  if(numberOfDots === 1) {
    firstPoint.left = event.pageX;
    firstPoint.top = event.pageY;
  }
  
  if(pointA.left && pointA.top && pointB.left && pointB.top) {
                let c=document.getElementById("myCanvas");
                let cxt=c.getContext("2d");
                        cxt.moveTo(pointA.left, pointA.top);
                        cxt.lineTo(pointB.left, pointB.top);
                        cxt.stroke();
    if(numberOfDots === 4) {
      cxt.moveTo(firstPoint.left, firstPoint.top);
                        cxt.lineTo(pointB.left, pointB.top);
                        cxt.stroke();
    }

    pointA.left = pointB.left;
    pointA.top = pointB.top;
    pointB = {left: 0, top:0}
    if(numberOfDots >= 4) {
      pointA = {left: 0, top:0}
      pointB = {left: 0, top:0}
      numberOfDots = 0
    }
  }
  document.body.appendChild(box);
  }
</script>

<style>
.box {
  padding: 7px;
  border-radius: 10px;
  margin-left: -10px;
  margin-top: -10px;
  background-color: Green;
  position: absolute;
}

#myCanvas {
   margin-left: -13px;
  margin-top: -14px;
  padding: 3px;
}

</style>

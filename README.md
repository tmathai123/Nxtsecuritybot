# Nxtsecuritybot
Security bot
<!DOCTYPE html>
<html>
<head>
<meta charset="ISO-8859-1">
<title>Smartlab Cam</title>
<script type="text/javascript" src="jquery.js"></script>       
<script type="text/javascript">
	$(document).ready(function() {
	   $("#left").mousedown(function() {
	     $.get('left');
	   });
	   $("#left").mouseup(function() {
		     $.get('stop');
	   });
	   $("#up").mousedown(function() {
		  $.get('up');
	   });
	   $("#up").mouseup(function() {
		     $.get('stop');
	   });
	   $("#down").mousedown(function() {
		  $.get('down');
	   });
	   $("#down").mouseup(function() {
		     $.get('stop');
	   });
	   $("#right").mousedown(function() {
		  $.get('right');
	   });
	   $("#right").mouseup(function() {
		     $.get('stop');
	   });
	});

	var pwd = "";

	function start() {	
		pwd = prompt("Password");
		setTimeout("update()", 1000);
		var drawingCanvas =
document.getElementById('canvas');
	
		drawingCanvas.width  = window.innerWidth;
		drawingCanvas.height = window.innerHeight / 2;
	}

	function update () {
		var drawingCanvas =
 document.getElementById('canvas');

		// Check the element is in the DOM 
 // and the browser supports canvas
		if(drawingCanvas.getContext) {
			// Initaliase a 2-dimensional drawing context
			var context =
                           drawingCanvas.getContext('2d');
			//Canvas commands go here

			var cam = new Image();
			cam.onload = function() {
			   context.drawImage(cam, 0, 0,
                                       cam.width, cam.height);
			}
			cam.src = 'cam.jpg?pwd=' + pwd;
			setTimeout("update()", 500);
		}

	}
</script>

</head>
<body onload="start()">
	<center>
	<table>
	<tr>
		<td>
		<a href="http://www.smartlab.at">
			<img src="header.jpg"/>
		</a>
		</td>
		<td>
			<img width="100" src="nxt_s.png"/>
		</td>
	</tr>
	</table>
	<div>
	<canvas id="canvas">
		<p>Your browser doesn't support canvas.</p>
	</canvas>
	</div>
	<table>
	<tr>
		<td>
			<img id='left' src="left.png"/>
		</td>
		<td>
			<img id='up' src="up.png"/>
		</td>
		<td>
			<img id='down' src="down.png"/>
		</td>
		<td>
			<img id='right' src="right.png"/>
		</td>
	</tr>
	</table>
	</center>
</body>
</html>

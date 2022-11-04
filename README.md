<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>HOSPITAL GPS UKY</title>
	<link rel="stylesheet">
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.2.1/dist/css/bootstrap.min.css" rel="stylesheet">
    <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.2.1/dist/js/bootstrap.bundle.min.js"></script>
    <style>
        img {
                position: absolute;
                top:520px;
                left: 5px;
            }

        body {
                background: 		url(https://upload.wikimedia.org/wikipedia/commons/9/9a/Sample_Floorplan.jpg) repeat-x;

            }
        #myAnimation {
                width: 20px;
                height: 20px;
                position: absolute;
                background-color: rgb(0, 68, 255);
              }
                .anybutton1 {
                top:80%;
                left:50%;
                width:100px;
                height:40px;
                position: absolute;
                z-index: 20;
              }
              .anybutton2 {
                top:80%;
                left:60%;
                width:100px;
                height:40px;
                position: absolute;
                z-index: 30;
              }

              .anybutton3 {
                top:80%;
                left:70%;
                width:100px;
                height:40px;
                position: absolute;
                z-index: 40;
              } 
              .btnHolder {
                position: relative;
              }             



    </style>

  <link rel="stylesheet" href="./node_modules/photo-sphere-viewer/dist/photo-sphere-viewer.css"/> <!-- Load in .css file -->
</head>
<body>
    <nav class="navbar navbar-expand-lg navbar-primary bg-primary">
        <div class="container-fluid">
          <a class="navbar-brand" href="#">Hospital GPS</a>
          <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarNavDarkDropdown" aria-controls="navbarNavDarkDropdown" aria-expanded="false" aria-label="Toggle navigation">
            <span class="navbar-toggler-icon"></span>
          </button>
          <div class="collapse navbar-collapse" id="navbarNavDarkDropdown">
            <ul class="navbar-nav">
              <li class="nav-item dropdown">
                <a class="nav-link dropdown-toggle" href="#" id="navbarDarkDropdownMenuLink" role="button" data-bs-toggle="dropdown" aria-expanded="false">
                  Destinations
                </a>
                <ul class="dropdown-menu dropdown-menu-dark" aria-labelledby="navbarDarkDropdownMenuLink">
                    {% for endpoint in endpoints %}
                        <li><a class="dropdown-item" href="#">{{ endpoint }}</a></li>
                    {% endfor %}
                </ul>
              </li>
            </ul>
          </div>
        </div>
      </nav>
      <div class="position-relative">
        <div class="position-absolute top-0 start-0"></div>
        <div class="position-absolute top-0 end-0"></div>
        <div class="position-absolute top-50 start-50"></div>
        <div class="position-absolute bottom-50 end-50"></div>
        <div class="position-absolute bottom-0 start-0"></div>
        <div class="position-absolute bottom-0 end-0"></div>
      </div>
 
      



<div class = "btnHolder"   >  
  
   <div class = "anybutton1">
    <button type="button" class="btn btn-secondary btn-lg">BACK</button>
  </div>

  <div class = "anybutton2">
    <button onclick = "myMove()" type="button" class="btn btn-primary btn-lg">NEXT</button>
  </div>

  <div class = "anybutton3">
    <button onclick="toggleViewer()" id=dim_button class="btn btn-secondary btn-lg" >3D-View</button>
  </div>


</div>
    <img src="https://img.freepik.com/free-photo/blurred-abstract-background-interior-view-looking-out-toward-empty-office-lobby-entrance-doors-glass-curtain-wall-with-frame_1339-6370.jpg?w=996&t=st=1665948644~exp=1665949244~hmac=be09c965a4642191e1ae612e16fb501d76aacf89968fc0249420c5644b802cdf" class="float-start rounded" width="200" height="200">  

    <div id ="myAnimation"></div>
<!-- Load in the photosphere dependencies -->
<script src="./node_modules/three/build/three.min.js"></script>
<script src="./node_modules/uevent/browser.js"></script>
<script src="./node_modules/photo-sphere-viewer/dist/photo-sphere-viewer.js"></script>

<!-- Definne the size of the viewer -->
<div id="viewer" style="width: 50vw; height: 50vh;"></div>


<!-- Initialize a Photo viewer -->
<!-- Still not fuctional currently -->
<script>
  /*
   * Function toggles the dimension of the view between 2-d and 3-d for the user upon click of button 
   * Bug: Once the viewer is removed it cannot be recovered // looking into documentation abouth either photosphere viewer 
   * // or a way to hide element instead of remove 
  */
  function toggleViewer() {
    var t = document.getElementById("dim_button");
    if (t.innerHTML == "3D-View"){ // if the view is 2-D 
      t.innerHTML = "2-D View"; // Set the button to new 2-D value 
      let viewer = new PhotoSphereViewer.Viewer({ // initialize new photosphereviewer 
        container: document.querySelector('#viewer'),
        panorama: '',
      });
    }
    else { // view in 3-d 
      t.innerHTML = "3D-View"; // switch the button and remove the viewer 
      viewer.remove()
    }
}
</script>

<script>
  var id = null;
  function myMove() {
    var elem = document.getElementById("myAnimation");   
    var pos = 14;
    clearInterval(id);
    id = setInterval(frame, 10);
    function frame() {
      if (pos == 350) {
        clearInterval(id);
      } else {
        pos++; 
        elem.style.top = pos + 'px'; 
        elem.style.left = pos + 'px'; 
      }
    }
  }
  </script>

<script src="gps.js"></script>
<script src='js.js'></script>

</body>
</html>

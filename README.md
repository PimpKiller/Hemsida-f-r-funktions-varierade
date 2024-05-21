Jag gjorde en exempel sida för att presenter min marzipano lösning här är start sidan så inte alla kan komma in och kolla:
 

Sedan kommer man till denna sidan:
 
Man kan navigera med panelen till vänster eller genom att klicka runt. panelens html kode ser ut så här:
<div id="sceneList">
  <ul class="scenes">
    
      <a href="javascript:void(0)" class="scene" data-id="0-grupprum-vid-svets">
        <li class="text">grupprum vid svets</li>
      </a>
    
      <a href="javascript:void(0)" class="scene" data-id="1-hall">
        <li class="text">hall</li>
      </a>
    
      <a href="javascript:void(0)" class="scene" data-id="2-im-botten-1">
        <li class="text">IM botten 1</li>
      </a>
    
      <a href="javascript:void(0)" class="scene" data-id="3-im-botten-2">
        <li class="text">IM botten 2</li>
      </a>
    
      <a href="javascript:void(0)" class="scene" data-id="4-im-botten-3-pingisbord">
        <li class="text">IM botten 3 (pingisbord)</li>
      </a>
      <a>  <li>  etc </li>  </a>
      <a>  <li>  etc </li>  </a>

      <a>  <li>  etc </li>  </a>

      <a>  <li>  etc </li>  </a>



  </ul>
</div>

CSS koden för panelen: 
#sceneList {
  position: absolute;
  top: 0;
  left: -220px;
  padding-top: 40px;
  width: 220px;
  max-height: 100%;
  overflow-x: hidden;
  overflow-y: auto;
  margin-left: 0;
  -webkit-transition: margin-left 0.5s ease-in-out;
  transition: margin-left 0.5s ease-in-out;
}

.mobile #sceneList {
  padding-top: 50px;
}

#sceneList .scenes {
  width: 100%;
  background-color: rgb(58,68,84);
  background-color: rgba(58,68,84,0.8);
}

.mobile #sceneList {
  width: 100%;
  height: 100%;
  left: -100%;
}

.mobile #sceneList.enabled {
  margin-left: 100%;
}

.mobile #sceneList .scenes {
  height: 100%;
}

#sceneList.enabled {
  margin-left: 220px;
}

#sceneList .scene {
  display: block;
  width: 100%;
  height: 30px;
}

.mobile #sceneList .scene {
  height: 40px;
}

#sceneList .scene .text {
  width: 100%;
  height: 100%;
  padding: 0 15px;
  line-height: 30px;
  overflow: hidden;
  text-overflow: ellipsis;
  white-space: nowrap;
}

.mobile #sceneList .scene .text {
  line-height: 40px;
}

.no-touch #sceneList .scene:hover {
  background-color: rgb(103,115,131);
  background-color: rgba(103,115,131,0.8);
}

#sceneList .scene.current {
  background-color: rgb(103,115,131);
  background-color: rgba(103,115,131,0.8);
}

/* Hide scene list when only a single scene exists */
body.single-scene #sceneList, body.single-scene #sceneListToggle {
  display: none;
}





Java koden jag använde för att bestämma hur de individuella bilderna skulle presenteras på hemsidan och delvist hur dom länkar ihop:
{
      "id": "0-grupprum-vid-svets",
      "name": "grupprum vid svets",
      "levels": [
        {
          "tileSize": 256,
          "size": 256,
          "fallbackOnly": true
        },
        {
          "tileSize": 512,
          "size": 512
        },
        {
          "tileSize": 512,
          "size": 1024
        },
        {
          "tileSize": 512,
          "size": 2048
        },
        {
          "tileSize": 512,
          "size": 4096
        }
      ],
      "faceSize": 2992,
      "initialViewParameters": {
        "yaw": -2.7388047317090063,
        "pitch": 0.4502125596265252,
        "fov": 1.2543877506952101
      },
      "linkHotspots": [
        {
          "yaw": 2.8490971566019283,
          "pitch": 0.20188559597016287,
          "rotation": 0,
          "target": "28-svets-korridor"
        }
      ],
      "infoHotspots": []
    },


Html koden för inlogningsidan:
 
   <!DOCTYPE html>
<html>
<head>
    <title>Login page</title>
</head>
<body>
<form>
    <label for="pswd">Enter your password: </label>
    <input type="password" id="pswd">
    <input type="button" value="Submit" onclick="checkPswd();" />
</form>
<!--Function to check password the already set password is admin-->
<script type="text/javascript">
    function checkPswd() {
        var confirmPassword = "admin";
        var password = document.getElementById("pswd").value;
        if (password == confirmPassword) {
             window.location="index.html";
        }
        else{
            alert("Passwords do not match.");
        }
    }
</script>
</body>
</html>




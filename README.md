"# Simple-Encryption-web-page" 
<!DOCTYPE html>
<html>
    <head>
        <meta charset="utf-8">
        <meta name="viewport" content="initial-scale=1, maximum-scale=1, user-scalable=no, width=device-width">
        <title>Blank App</title>
        <style>
            textarea {
                width: 95%;
                height: 12.500em;
                background-color: #E8E7E4;
                color: #07034A;
                font-size: 15px;
                resize: none;
            }
            .input2{
                width: 40%;
                height: 30px;
                background-color: #E8E7E4;
                color: #07034A;
                font-size: 30px;
            }
            .but{
                margin-top: 1.250em;
                width:6.0em;
                height 1.250em;
                background-color: #E8E7E4;
                color: #07034A;
                font-size: 1.em;
            }
            .par{
                width: 80%;
                font-size: 1.em;
                word-wrap: break-word;
                text-align: center;
            }
        </style>
        <script>
            var s = ['!','"','#','$','%','&',',','(',')','*','+',',','-','.','/','0','1','2','3','4','5','6','7','8','9',':',';','<','=','>','?','@','A','B','C','D','E','F','G','H','I','J','K','L','M','N','O','P','Q','R','S','T','U','V','W','X','Y','Z','[',']','^','_',"`",'a','b','c','d','e','f','g','h','i','j','k','l','m','n','o','p','q','r','s','t','u','v','w','x','y','z','{','|','}','~'," "];
            
         function Gettext(){
            var posting = document.getElementById("thing").value;
             var numstring = [];
             for (var j = 0; j < posting.length;j++){
                 for( var i = 0; i <= 126; i++ ){
                     if(posting[j] == s[i]){
                     numstring[j] = i;
                     }
                 }
            }
            var A = parseInt(document.getElementById("A").value);
            var B = parseInt(document.getElementById("B").value);
             for (var j = 0; j < posting.length;j++){
                 numstring[j] = ((A)*numstring[j] + B)%s.length;
             }
             var encript = " ";
             for (var j = 0; j < posting.length;j++){
                 for( var i = 0; i <= 126; i++ ){
                     if(numstring[j] == i){
                     encript += s[i];
                     }
                 }
            }
             
            var currpost = document.getElementById("postbox").innerHTML;
            currpost += "<br>" + " "+ encript;
            document.getElementById("postbox").innerHTML = currpost;
        }
           function Decript(){
               var posting = document.getElementById("thing").value;
               var numstring = [];
             for (var j = 0; j < posting.length;j++){
                 for( var i = 0; i <= 126; i++ ){
                     if(posting[j] == s[i]){
                     numstring[j] = i;
                     }
                 }
            }
             var A = parseInt(document.getElementById("A").value);
            var B = parseInt(document.getElementById("B").value);
               var tyo = false;
               for(var i = 0; tyo != true && i != s.length; i++ ){
                   var test = (A*i)%s.length;
                     if (test == 1){
                         A = i;
                         tyo = true;
                     }
                 }
               if(s.length == i){
                   encript = "sorry this dosent work as keys"
               }else{
               i = i -1;
               for (var j = 0; j < posting.length;j++){
                 numstring[j] = (i*(numstring[j] - B))%s.length;
             }
               
             var encript = " ";
             for (var j = 0; j < posting.length;j++){
                 for( var i = 0; i <= 126; i++ ){
                     if(numstring[j] == i){
                     encript += s[i];
                     }
                 }
            }
            }
            var currpost = document.getElementById("postbox").innerHTML;
            currpost += "<br>" + " "+ encript;
            document.getElementById("postbox").innerHTML = currpost;
                   
           } 
            function Cleartext(){
                document.getElementById("postbox").innerHTML = " ";
            }
            function genkey(){
                var encript = "keys are = "
                for (var A = 0;A <s.length;A++){
                    var tyo = false;
                    for(var i = 0; tyo != true && i != s.length; i++ ){
                       var test = (A*i)%s.length;
                         if (test == 1){
                             A = i;
                             tyo = true;
                         }
                     }
                   if(tyo == true){
                      encript += A + ",";
                }
            }
            var currpost = document.getElementById("postbox").innerHTML;
            currpost += "<br>" + " "+ encript;
            document.getElementById("postbox").innerHTML = currpost;
            }
        </script>
    </head>
    <body>
        <script type="text/javascript" src="cordova.js"></script>
        <textarea type="text" id="thing" name="String" class="input"></textarea><br><center>
        <input type="number" id="A" name="Key 1 num please" class="input2">
        <input type="number" id="B" name="Key 2 num please" class="input2"><br>
        <button onclick="Gettext();" class="but">Encript</button>
        <button onclick="Decript();" class="but">Decript</button>
        <button onclick="genkey();" class="but">Gen Key</button>
        <button onclick="Cleartext();" class="but">Clear Box</button>
        <p id="postbox" class="par"></p></center>
        
    </body>
</html>


test
====

&lt;html> 	&lt;head> 	 &lt;script src="http://ajax.googleapis.com/ajax/libs/jquery/1.11.1/jquery.min.js">&lt;/script> 	&lt;/head> 	&lt;body> 		&lt;div id="result">&lt;/div>  		&lt;script> 			var string = 'aabbaddgdfgfbbbfgsdfgsdfgsbbbbcccdd'; 			var uinqData = string.replace(/(.)(?=.*\1)/g, "") 			var obj ={}; 			for(var i=0;i&lt;uinqData.length;i++){ 			    ele = uinqData.charAt(i); 			    regex = new RegExp(ele, 'g' ); 			    count = string.match(regex).length; 			    $("#result").append(ele + " is repeated " + count + " times"+"&lt;br/>"); 			      			}  			// $.each(obj, function(key, value){ 			//   $("#result").append(key + " is repeated " + value + " times"+"&lt;br/>"); 			// }); 		&lt;/script> 	&lt;/body> &lt;/html>






...........................LiftCode....................................................................................

<html lang="en">
<head>
  <meta charset="utf-8">
  <title>animate demo</title>
  <style>
    .block {
      position: absolute;
      background-color: #abc;
      bottom: 0;
      width: 90px;
      height: 87px;
      margin: 5px;
    }
    .switch_block{
      position: absolute;
      left: 50px;
      width: 100px;
      height: 450px;
      margin: 5px;
    }
    .building {
      position: absolute;
      border: 1px solid red;
      left: 150px;
      width: 100px;
      height: 459px;
      margin: 5px;
    }
    .moving_sign{
      border: 1px solid #D3D3D3;
      border-radius: 4px;
      height: 20px;
      margin-top: 10px;
      width: 20px;
    }
    .up{
      /*padding: 0 3px 5px 8px;*/
    }
    .down {
      /*padding: 0 3px 5px 8px;*/
    }
    .on{
       background-color: green;
    }
    .floor{
      padding: 10px;
      margin-top: 5px;
    }
    #fourth_floar{
      margin-top: 94px;
    }
    #third_floar{
      margin-top: 90px;
    }
    #second_floar{
      margin-top: 88px;
    }
    #first_floar{
      margin-top: 87px;
    }

    .top_down_sigh{
      margin-top: 34px;
      margin-left: 20px;
    }
    .third_up_sigh{
      margin-bottom: -37px;
      margin-top: 65px;
      margin-left: 20px;
    }
    
    .third_down_sigh{
       margin-top: 36px;
      margin-bottom: -10px;
       margin-left: 20px;
    }
    .second_up_sigh{
       margin-bottom: -37px;
      margin-top: 61px;
      margin-left: 20px;
    }
    .second_down_sigh{
       margin-top: 36px;
      margin-bottom: -10px;
       margin-left: 20px;
    }
    .bottom_up_sigh{
       margin-top: 58px;
      margin-bottom: -10px;
      margin-left: 20px;
    }

    .first_up_sigh{
       margin-top: 48px;
      margin-bottom: -10px;
      margin-left: 20px;
    }
  .first_down_sigh{
     margin-left: 20px;
  }
  </style>
  <script src="http://code.jquery.com/jquery-1.11.0.min.js"></script>
</head>
<body>
<div class="lift_block">
  <div class="switch_block" style="float:left">
    <div class="btn-block" style="float:left">

      <button id="floor4" data-floor="4" class="floor">F4</button><br/>
      <button id="floor3" data-floor="3" class="floor">F3</button><br/>
      <button id="floor2" data-floor="2" class="floor">F2</button><br/>
      <button id="floor1" data-floor="1" class="floor">F1</button><br/>
      <button id="floor0" data-floor="0" class="floor">F0</button>
    </div>
    <div class="moving_status" style="float:left; margin-left: 10px;">

       
       <div class="moving_sign down top_down_sigh" id="down_moving_sign">&#x25BC;</div>
       <div class="moving_sign up third_up_sigh" id="up_moving_sign">&#x25B2;</div>
       <div class="moving_sign down third_down_sigh" id="down_moving_sign">&#x25BC;</div>
       <div class="moving_sign up second_up_sigh" id="up_moving_sign">&#x25B2;</div>
       <div class="moving_sign down second_down_sigh" id="down_moving_sign">&#x25BC;</div>
       <div class="moving_sign up first_up_sigh" id="up_moving_sign">&#x25B2;</div>
       <div class="moving_sign down first_down_sigh" id="down_moving_sign">&#x25BC;</div>
       <div class="moving_sign up bottom_up_sigh" id="up_moving_sign">&#x25B2;</div>
       
    </div>
  </div>
  <div class="building" style="float:left">
    <hr id="fourth_floar">
    <hr id='third_floar'>
    <hr id='second_floar'>
    <hr id='first_floar'>
    <div class="block" data-currentfloor="0">
    </div>
  </div>
</div>
 
<script>
 var moving_position = [];
 $( ".floor" ).click(function() {
   var target_floor = $(this).data('floor');
   moving_position.push(target_floor);
 });
 var move = function(){
  if(moving_position.length > 0){
    var current_floor = $(".block").attr('data-currentfloor');
    console.log(moving_position);
    var target_floor =  moving_position.shift();
    var move_space = 0;
    if(target_floor > current_floor){
      move_space = (target_floor - current_floor)*90;
      $( ".block" ).animate(
        { "top": "-=" + move_space + "px" },
        2000, "linear", function() {
          $( ".block" ).text("moving to floor : " + target_floor); 
        }
      );
      $("#down_moving_sign").removeClass('on');
      $("#up_moving_sign").addClass('on');
    }else{
      move_space = (current_floor - target_floor)*90;
      $( ".block" ).animate(
        { "top": "+=" + move_space + "px" },
        2000, "linear", function() {
          $( ".block" ).text("moving to floor : " + target_floor); 
        }
      );
      $("#up_moving_sign").removeClass('on');
      $("#down_moving_sign").addClass('on');
    }
    $( ".block").attr('data-currentfloor', target_floor);
   }
 }
 setInterval(function(){move();},500);


</script>
 
</body>
</html>
...................................................................................................




















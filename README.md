test
====

&lt;html> 	&lt;head> 	 &lt;script src="http://ajax.googleapis.com/ajax/libs/jquery/1.11.1/jquery.min.js">&lt;/script> 	&lt;/head> 	&lt;body> 		&lt;div id="result">&lt;/div>  		&lt;script> 			var string = 'aabbaddgdfgfbbbfgsdfgsdfgsbbbbcccdd'; 			var uinqData = string.replace(/(.)(?=.*\1)/g, "") 			var obj ={}; 			for(var i=0;i&lt;uinqData.length;i++){ 			    ele = uinqData.charAt(i); 			    regex = new RegExp(ele, 'g' ); 			    count = string.match(regex).length; 			    $("#result").append(ele + " is repeated " + count + " times"+"&lt;br/>"); 			      			}  			// $.each(obj, function(key, value){ 			//   $("#result").append(key + " is repeated " + value + " times"+"&lt;br/>"); 			// }); 		&lt;/script> 	&lt;/body> &lt;/html>



























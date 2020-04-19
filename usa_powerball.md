---
layout: page
title: USA Powerball
permalink: /USA_powerball/
---
<center><img style="max-width: 50%" src="/assets/usa-powerball.png"></center>

<center><h1>USA Powerball Number Generator</h1></center>
<center><h5 style='margin-bottom:0px;'>Generate a total of 6 digits of the lotto number. <br> 
The number is created through up to 5 times, and you can <b>refresh</b> it if you want.<br>
<b>Please purchase a lottery ticket using a screen capture</b></h5></center>

<!-- Kakao AdFit -->
<ins class="kakao_ad_area" style="display:none;" 
 data-ad-unit    = "DAN-t4nbyr8xmxbp" 
 data-ad-width   = "320" 
 data-ad-height  = "100"></ins> 
<script type="text/javascript" src="//t1.daumcdn.net/kas/static/ba.min.js" async></script>

<div class="div_canvas">
    <center><canvas id="canvas-sample"></canvas></center>
</div>
<div id="div-button">
<center><button id="btn_generator" type="button" class="generator" style='margin-bottom:15px;'  onclick="window.generator()">Generate Number</button></center>
</div>


<!-- Google Adsense -->
<script async src="https://pagead2.googlesyndication.com/pagead/js/adsbygoogle.js"></script>
<ins class="adsbygoogle"
     style="display:block; text-align:center;"
     data-ad-layout="in-article"
     data-ad-format="fluid"
     data-ad-client="ca-pub-5547143505780462"
     data-ad-slot="1196095930"></ins>
<script>
     (adsbygoogle = window.adsbygoogle || []).push({});
</script>

<script>
    var num_of_generator = 0;
    window.generator = function() {
        if (num_of_generator > 4) {
            var btn = document.getElementById("btn_generator")
            btn.innerHTML = "Refresh"
            btn.onclick = function() {
                location.reload();
            }
            return;
        }
        var center = document.createElement("center")

        var div = document.createElement("div")
        div.id = "div_lotto_canvas"

        var canvas = document.createElement("canvas")
        let canvasID = "canvas-lotto-" + String(num_of_generator)
        num_of_generator += 1;
        canvas.id = canvasID
        //document.getElementById("btn_generator").innerHTML += '<center><canvas id="canvas"></canvas></center>';
        center.appendChild(canvas)
        div.appendChild(center)
        console.log(div)
        document.getElementById("div-button").appendChild(div)
        
        lotto_numbers = generate(5, 1, 69) + " / " + generate(1, 1, 26)
        console.log(lotto_numbers)
        var numbers = document.createElement("h5")
        numbers.style.cssText='color:black; text-align: center;';
        numbers.innerHTML = lotto_numbers + "<br>";   
        //var numbers_text = document.createTextNode(lotto_numbers);
        //numbers.appendChild(numbers_text);
        document.getElementById("div-button").appendChild(numbers)
        console.log(numbers)
        lotto_numbers = String(lotto_numbers).split(',').join('  ');
        text_particle(canvasID, lotto_numbers)
    }

    function generate(size, lowest, highest) {
            var numbers = [];
            for(var i = 0; i < size; i++) {
                var add = true;
                var randomNumber = Math.floor(Math.random() * highest) + 1;
                for(var y = 0; y < highest; y++) {
                    if(numbers[y] == randomNumber) {
                        add = false;
                    }
                }
                if(add) {
                    numbers.push(randomNumber);
                } else {
                    i--;
                }
            }
        
            var highestNumber = 0;
            for(var m = 0; m < numbers.length; m++) {
                for(var n = m + 1; n < numbers.length; n++) {
                    if(numbers[n] < numbers[m]) {
                        highestNumber = numbers[m];
                        numbers[m] = numbers[n];
                        numbers[n] = highestNumber;
                    }
                }
            }
            return numbers
    }
</script>
<script type="text/javascript" src="js/text_particle.js"></script>

---
layout: page
title: 대한민국 연금복권
permalink: /Korean2/
---
<center><img style="max-width: 50%" src="/assets/korean_lottery2.jpg"></center>

<center><h1>번호 생성기</h1></center>
<center><h5 style='margin-bottom:0px;'>연금 복권 번호 총 7자리를 생성합니다.<br> 
최대 5개까지 생성이 되며, 추가로 원하시면 <b>새로고침</b>됩니다.<br>
<b>화면 캡처를 이용해 복권을 구매하세요</b></h5></center>

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
<center><button id="btn_generator" type="button" style='margin-bottom:15px;' class="generator" onclick="window.generator()">번호 생성</button></center>
</div>
<script async src="https://pagead2.googlesyndication.com/pagead/js/adsbygoogle.js"></script>

<!-- Google Adsense -->
<script data-ad-client="ca-pub-5547143505780462" async src="https://pagead2.googlesyndication.com/pagead/js/adsbygoogle.js"></script>
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
            btn.innerHTML = "새로 고침"
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
        
        lotto_numbers = generate(1, 1, 7) + '조  ' + generate(1, 4, 9) + '  ' + generate(5, 0, 9)
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

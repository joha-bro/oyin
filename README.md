<!DOCTYPE html>
<html lang="en">

<head>
    <title>Document</title>
    <style>
        
        
        .box {
            width: 520px;
            height:520px;
            display: flex;
            margin: 25px;
            
        }

        .katak {
            width: 150px;
            height: 150px;
            background-color: rgb(119, 69, 69);
            margin: 5px;
    
            font-size: 90pt;
            text-align: center;
            color: rgb(200, 188, 188);
            border-radius: 20px;
            box-shadow: 4px 4px 4px 4px;

        }
    </style>
</head>

<body>
    <div class="box">
        <div class="miniBox">
            <div id="1" class="katak" onclick="chizish(this)"></div>
            <div id="4" class="katak" onclick="chizish(this)"></div>
            <div id="7" class="katak" onclick="chizish(this)"></div>
        </div>
        <div class="miniBox">
            <div id="2" class="katak" onclick="chizish(this)"></div>
            <div id="5" class="katak" onclick="chizish(this)"></div>
            <div id="8" class="katak" onclick="chizish(this)"></div>
        </div>
        <div class="miniBox">
            <div id="3" class="katak" onclick="chizish(this)"></div>
            <div id="6" class="katak" onclick="chizish(this)"></div>
            <div id="9" class="katak" onclick="chizish(this)"></div>
        </div>
    </div>

    <script>

        combinatsiyalar =
            [
                [1, 2, 3], [4, 5, 6], [7, 8, 9],
                [1, 4, 7], [2, 5, 8], [3, 6, 9],
                [1, 5, 9], [3, 5, 7]
            ]

        let belgi = "X"
        function chizish(bosilganDiv) {
            if (bosilganDiv.innerHTML == '') {
                bosilganDiv.innerHTML = belgi

                // Yutiqni aniqlash
                let divlar = []
                for (i = 1; i <= 9; i++) {
                    divlar[i] = document.getElementById(i)
                }

                for (i = 0; i < combinatsiyalar.length; i++) {
                    let yutuqniAniqlash = 0
                    for (j = 0; j < 3; j++) {
                        if (divlar[combinatsiyalar[i][j]].innerText == belgi) {
                            yutuqniAniqlash += 1
                        }
                    }
                    if (yutuqniAniqlash == 3) {
                        setTimeout(function() {
                            alert(belgi + " siz yutdingiz!")
                            qaytaBoshlash()
                        }, 100)
                        return
                    }
                }

                belgi = belgi == "X" ? "O" : "X"

                // durrangni tekshirish
                let durrang = true;
                for (let i = 1; i <= 9; i++) {
                    if (divlar[i].innerHTML == '') {
                        durrang = false
                        break
                    }
                }

                if (durrang) {
                    setTimeout(function() {
                        alert("O'yin durrang bo'ldi!")
                        qaytaBoshlash()
                    }, 100) 
                    return
                }
            }
        }

        function qaytaBoshlash() {
            for (let i = 1; i <= 9; i++) {
                document.getElementById(i).innerHTML = '';
            }
            belgi = "X"; 
        }
    </script>
</body>

</html>

## 1st Assignment -OnePage ShoppingMall
* Change every font to 'Hi Melody'
* Body setting
```
* {
            font-family: 'Hi Melody', cursive;
        }
body {
            background-color: #fcb4da;
            padding-right: 30px;
            padding-left: 30px;
        }
```
* Image aligned center and set padding 20px
```
<section class="img">
    <img src="사진 url">
</section>

.img {
            display: flex;
            align-items: center;
            justify-content: center;
            padding: 20px;
        }
```
* When the size of the site diminishes, b would aligned next to the title
* p doesn't move and take up the space
```
<section>
    <h1>구름 &#9729판매중&#9729</h1>
    <p class="b">가격: <b>1,000,000원</b> / 개</p>
    <div class="product-describe">
        <p>최고급 구름으로 새하얗고 폭신폭신하며 보드랍고 달콤하죠. 구름빵을 만들고 싶다면 필수적으로 구매해야 합니다.
            10구름을 구매하신다면 2구름을 무료로 더 드립니다. 사실 구름빵을 만들지 않더라도 그냥 그 자체로도
            솜사탕보다도 맛있답니다. 어서 빨리 품절되기 전에 구매하세요!</p>
    </div>
</section>

h1 {
            font-weight: bold;
            color: #4288E9;
            margin: 20px auto;
            padding-left: 20%;
            display: inline-block;
        }

p {
            font-size: 1.5em;
        }

.b {
            display: inline-block;
        }

.product-describe {

            max-width: 800px;
            display: block;
            margin-left: auto;
            margin-right: auto;
        }
```
* Similar with b, exchange would aligned next to the title but always
* Using <table border="0" align="center" width=auto cellpadding="8">, label and input would aligned well
* oninput made input to show it's current value
+ PROBLEM: Whenever slide the range point, the whole order-table class shakes. But I like the way it shakes so I just left it
```
<section>
    <div class="order-title">
        <h1>주문하기</h1>
        <p class="exchange" style="display:inline-block; color: red">환율 계산기: </p>
    </div>
    <div class="order-table" style="padding-bottom: 25px">
        <table border="0" align="center" width=auto cellpadding="8">
            <tr>
                <td><label class="c-name">주문자 성함: </label></td>
                <td><input type="text" class="c-name" id="c-name" size="30"></td>
            </tr>
            <tr>
                <td><label class="c-num">수량: </label></td>
                <td><input type="range" class="c-num" id="c-num"
                           tep="1" value="1" min="1" max="10"
                           oninput="this.nextElementSibling.value = this.value">
                    <output style="font-size: 1.5em">1</output>
                </td>
            </tr>
            <tr>
                <td>
                    <label class="c-address">주소: </label></td>
                <td>
                    <input type="text" class="c-address" id="c-address" size="30">
                </td>
            </tr>
            <tr>
                <td>
                    <label class="c-phone">전화번호: </label></td>
                <td>
                    <input type="tel" class="c-phone" id="c-phone" size="30">
                </td>
            </tr>
        </table>
    </div>
</section>

#c-num {
            width: 200px;
        }
```
```
<section style="padding-bottom: 25px; text-align: center">
    <button onclick="order()" type="button" class="order">주문하기</button>
</section>
```
```
button {
            width: 80px;
            background-color: #4288E9;
            color: floralwhite;
            border: none;
            border-radius: 10px;
        }
```
```
function order() {
            alert("주문이 완료되었습니다 *^^*");
        }
```
* As soon as page is loaded, alert shows automatically
```
$(document).ready(function () {
            calculator();
        })

        function calculator() {
            $.ajax({
                type: "GET",
                url: "http://spartacodingclub.shop/sparta_api/rate",
                data: {},
                success: function (response) {
                    let change = response['rate']
                    change_html = `1$=${change}&#x20a9;`
                    $('.exchange').append(change_html)
                }
            })
        }
```

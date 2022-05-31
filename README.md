## 1st&2nd Assignment -OnePage ShoppingMall
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
## <1주차 회고록>
```
CSS는 파일로 따로 만들기보다 <style>로 가능 (<link rel="stylesheet" type="text/css" href = "(css파일이름).css">로 파일 분리 가능)
<section>을 반복적으로 사용하는 것은 <div>만 사용하기보다 효율적일 수 O
대부분의 개발환경에서 ctrl + /을 누르면 자동으로 주석처리
```
```
# -> id 선택, . -> class 선택 
padding: 안쪽 여백 설정
margin: 바깥 여백 설정
display: grid, block(언제나 새로운 라인, 모든 라인 차지), inline-block, inline(현재 라인에서 시작, 내용만큼만 차지)
가운데 정렬: magin auto, 
<form></form> 태그 안에 버튼이 있으면 자동 새로고침 --> <div></div>로 바꿔주면 해결
```
```
부트스트랩 시작 템플릿
<html>
<!doctype html>
<html lang="en">

<head>
    <!-- Required meta tags -->
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width, initial-scale=1, shrink-to-fit=no">

    <!-- Bootstrap CSS -->
    <link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/4.0.0/css/bootstrap.min.css"
        integrity="sha384-Gn5384xqQ1aoWXA+058RXPxPg6fy4IWvTNh0E263XmFcJlSAwiGgFAW/dAiS6JXm" crossorigin="anonymous">

    <!-- Optional JavaScript -->
    <!-- jQuery first, then Popper.js, then Bootstrap JS -->
    <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.5.1/jquery.min.js"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/popper.js/1.12.9/umd/popper.min.js"
        integrity="sha384-ApNbgh9B+Y1QKtv3Rn7W3mgPxhU9K/ScQsAP7hUibX39j7fakFPskvXusvfa0b4Q"
        crossorigin="anonymous"></script>
    <script src="https://maxcdn.bootstrapcdn.com/bootstrap/4.0.0/js/bootstrap.min.js"
        integrity="sha384-JZR6Spejh4U02d8jOt6vLEHfe/JQGiRRSQQxSfFWpi1MquVdAyjUar5+76PVCmYl"
        crossorigin="anonymous"></script>
</html>
```
## <2주차 회고록>
```            
<script></script> 내부에 javascript, ajax, jquery 활용
button onclick="hey()"로 버튼에 함수 연결 가능
console.log(변수(response)): 콘솔 창에 괄호 값 출력 --> 코드 한 줄마다 넣음으로써 오류 발견 가능
let 변수: 변수 선언(다른 언어의 int 같은)
.toUpperCase(): 대문자로 바꿔주기
.split(): 괄호 속 변수 기준으로 나누기
.join(): 괄호 속 변수로 문자 합치기        
```   
```            
jQuery: javascript계의 bootstrap (<script src="https://ajax.googleapis.com/ajax/libs/jquery/3.4.1/jquery.min.js"></script>로 임포트)
$('. or #').show(): 보이기
$('. or #').hide(): 숨기기
function 내부에 적어 활용 多
```
```            
$.ajax({
  type: "GET", // GET 방식으로 요청한다.
  url: "여기에URL을입력",
  data: {}, // 요청하면서 함께 줄 데이터 (GET 요청시엔 비워두세요)
  success: function(response){ // 서버에서 준 결과를 response라는 변수에 담음
    console.log(response) // 서버에서 준 결과를 이용해서 나머지 코드를 작성
  }
})
활용법: temp_html = `<li>${gu_name} : ${dust}</li>`                 $('#names-q1').append(temp_html) --> 버튼 누를 때마다 temp_html이 이전의 temp_html에 붙어서 출력
자꾸 temp_html에 ` 대신 ' 쓰는 실수를 반복적으로 저지름
attr: 함수=""의 "" 속에 붙여넣기
활용법: let pics = response[0]['url']              $('#img-cat').attr('src', pics) --> url인 pics를 src에 넣기
$(document).ready(function () {}): 로딩되자마자 불러오기
```            

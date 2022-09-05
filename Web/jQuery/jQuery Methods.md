## jQuery 적용 방법

### CDN 이용하기
#### [원하는 버전으로 다운 받기](https://releases.jquery.com/)
```
<script src="//code.jquery.com/jquery-3.3.1.min.js"></script>
```
### LOAD, READY
- LOAD : DOM, 이미지 등이 **모두** 로드되었을 때 실행됨(window.onload)
- READY : DOM이 로드되면 실행됨
	 ➞ $(document).ready() == $(function() {})
- 위와 같은 이유로 READY가 LOAD보다 **더 빠름**
```
// 두 개는 동일
$(document).ready(function() {
	console.log('load');
})
$(function() {
	console.log('$ ready');
})
```
### Selector
- 선택자를 쉽게 사용 가능
```
$('.classname') // 클래스 이름으로 요소 찾기
$('.classname li')
$('.classname').children() // 요소의 자식 찾기
$('.classname').children().parent() // 자식의 부모(본인) 찾기
```

### Find
- 찾은 요소의 자식 중 원하는 태그들 추출
```
// 두 개는 동일
$('.classname').find('li') // 찾은 요소의 자식 중 li 태그들을 찾아 냄
$('.classname li')
```

### eq
- 찾은 요소 리스트에서 n번째 인덱스 요소 추출
```
$('classname li').eq(1) // 해당 요소 리스트에서 첫 번째 인덱스
```

### index
- 해당 요소의 인덱스 반환
```
$(.classname).on('click', function() {
	var index = $('.classname').index(this);
	console.log(index);
}
```

### addClass, removeClass, hasClass
- 클래스명을 더하거나, 지우거나, 가지고 있는지 확인
```
$('.classname').addClass('active') // 해당 요소에 active 클래스 네임 추가
```

### remove, prepend, append, appendTo, wrap
- 엘리먼트 삭제, 자식의 첫번째 요소로 추가, 마지막 요소로 추가, 기존 요소를 감싸도록 함
```
$('.classname').remove(); // 해당 클래스네임의 요소 삭제
$('.classname').prepend('<li>첫번째 자식 요소</li>'); // 자식의 첫번째에 li 태그 추가
$('.classname').append('<li>마지막 자식 요소</li>'); // 자식의 마지막에 li 태그 추가
$('<li>마지막 자식 요소</li>').appendTo('.classname'); // 위와 동일
$('.classname').wrap('<div class="wrap">); // div 태그로 감싸짐
```

### css, removeAttr, attributing
- 엘리먼트의 스타일을 적용하고, 요소의 특정 속성 제거, 속성 지정하거나 가져오기 가능
```
$('.classname').css({ color: 'red' }); // 엘리먼트 스타일 적용
$('.classname').removeAttr('style'); // 스타일 속성 제거
$('.classname').attr('style', 'color:red'); // 속성 지정하기
console.log($('.classname').attr('style')); // 속성 가져오기
```

### each
- 요소를 반복하는 반복문
```
$('.classname').each(function(index, list) {
	// forEach 같은 반복문
})
```

### width, height, outerWidth, outerHeight
- 패딩을 제외한 너비, 패딩을 제외한 높이, 패딩을 합한 너비, 패딩을 합한 높이

### offset, position
- 요소의 좌표, 부모 기준 요소의 좌표
```
$('.classname').offset();
$('.classname').offset().top(); // left도 가능

$('.classname').position(); // top, left 가능
```

### text
- 엘리먼트의 텍스트 정보를 변경하거나 가져올 때 사용
```
$('.classname').text(); // 텍스트 내용 가져오기
$('.classname').text('바꾸려는 텍스트 값'); // 텍스트 값 바꾸기
```

### fade, fadeOut, hide, show, animate
- n시간에 걸쳐 다양한 애니메이션 동작을 하도록 지시하는 명령어
```
$('.classname').fadeOut(1000); // 1초에 걸쳐 페이드아웃
$('.classname').fadeIn(1000); // 1초에 걸쳐 페이드인

$('.classname').hide(1000); // 1초에 걸쳐 사라짐
$('.classname').show(1000); // 1초에 걸쳐 보여짐

$('.classname').slideUp(1000); // 위로 슬라이드됨
$('.classname').slideDown(1000); // 아래로 슬라이드됨

// 3초에 걸쳐 height가 300px로 변함, 실행이 끝나면 callback 함수가 실행됨
$('.classname').animate({ height: '300px'}, 3000, function() {console.log('call back 붙이기'}); 
```

### scrollLeft, scrollTop
- 가로 스크롤 위치, 세로 스크롤 위치 가져오기
```
console.log($('html').scrollLeft);
```

### event
- 요소에 이벤트 추가
```
$(window).scroll(function() {
	console.log('scroll event'); // 스크롤될 때마다 실행되는 콘솔
})
$(window).on('scroll', function() {
	console.log('scroll event');
})
$(window).resize(function() {
	console.log('resize event'); // 사이즈를 변경할 때마다 실행되는 콘솔
})

// click event
$(.classname).on('click', function() {
	console.log('클릭 :', $(this).text());
})

$('.classname).off(); // 이벤트 제거
```
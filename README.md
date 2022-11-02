# Making painting app by using Vanilla JS

Vanilla JS project for Practice Canvas API

프로젝트 진행 과정

1. mousedown 상태로 캔버스를 빠져나갔을때 캔버스로 돌아오면 클릭을 안하고 있음에도 불구하고 mousedown 상태 유지되는 버그를 mouseleave를 통해 해결하거나, canvas 대신 document에 mouseup 이벤트를 부여해서 버그 해결 가능. (해당 프로젝트에서는 mouseleave 추가로 해결)
2. colorOptions를 Array.from을 사용해서 배열로 만들면 forEach메소드 이용하여 이벤트리스너를 추가할 수 있다. 각 color마다 이벤트리스너를 추가하여 유저가 click한 색상을 그리거나 채울 수 있게 한다.
3. ctx.save()와 ctx.restore()를 활용하여 수정하기 직전상태를 저장하고 나서 수정 후에 바로 다시 저장해두었던 원래 상태로 되돌아갈 수 있게 만들었음.
4. ctx.lineCap = "round"; 을 이용하여 선의 끝모양을 둥글게 처리.
5. createObjectURL 메소드를 사용하여 해당 파일의 브라우저 메모리 URL을 알아낼 수 있고 이를 통해 이미지 로드를 하게 만들었음. 
6. 이후에 ctx.drawImage 메소드를 사용하여 캔버스 면적 크기 만큼의 이미지를 화면에 나타내었음. 
7. const url = canvas.toDataURL(); 이용하여 캔버스 그림을 URL로 인코딩하여 저장.
8. CSS처리.


*프로젝트 추가 희망 기능 업데이트 성공*

1. 텍스트 화면에 출력하는 부분에서 유저가 textstroke, textfill 두가지 텍스트 모드로 전환할 수 있도록 업데이트.
2. 화면에 드로잉 시에 유저가 drawstroke, drawfill 두가지 드로잉 모드로 전환할 수 있도록 업데이트.
3. 선그리다가 마우스업시 갑자기 fill로 전환

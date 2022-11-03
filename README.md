# Making painting app by using Vanilla JS

Vanilla JS project for Practice Canvas API

프로젝트 진행 과정 Key Point 요약

1. mousedown 상태로 캔버스를 빠져나갔을때 캔버스로 돌아오면 클릭을 안하고 있음에도 불구하고 mousedown 상태 유지되는 버그를 mouseleave를 통해 해결하거나, canvas 대신 document에 mouseup 이벤트를 부여해서 버그 해결 가능. (해당 프로젝트에서는 mouseleave 추가로 해결)
2. colorOptions를 Array.from을 사용해서 배열로 만들면 forEach메소드 이용하여 이벤트리스너를 추가할 수 있다. 각 color마다 이벤트리스너를 추가하여 유저가 click한 색상을 stroke하거나  fill 할 수 있게 한다.
3. ctx.save()와 ctx.restore()를 활용하여 수정하기 직전상태를 저장하고 나서 수정 후에 바로 직전에 저장해두었던 원래 상태로 되돌아갈 수 있게 만들었음.
4. ctx.lineCap = "round"; 을 이용하여 선의 끝모양을 둥글게 처리.
5. createObjectURL 메소드를 사용하여 해당 파일의 브라우저 메모리 URL을 알아낼 수 있고 이를 통해 이미지 로드를 하게 만들었음. 
6. 5.를 이용해서 이후 ctx.drawImage 메소드를 사용하여 캔버스 면적 크기 만큼의 이미지를 화면에 나타내었음. 
7. const url = canvas.toDataURL(); 이용하여 캔버스 그림을 URL로 인코딩하여 저장.
8. CSS처리.



*프로젝트 수정, 희망 기능 추가, 버그 해결 및 업데이트 성공 요약*

1. inputtext를 화면에 나타내는 부분에서 유저가 textstroke, textfill 두가지 텍스트 모드로 전환할 수 있도록 업데이트.
2. inputtext를 화면에 표시할때 fillscreen 상태인경우 첫 더블클릭시 fillscreen이 먼저 적용되어 inputtext가 화면에 바로 나타나지 않는 버그를 onCanvasClick에 isFilling = false; 추가해서 해결완료. 단, 이로 인해  onCanvasClick은 일회적인 특성을 가지게 되어서 유저가 fillscreen모드를 적용하기 희망할 때마다 매번 fillscreen 버튼을 클릭해야 함. 
3. drawfill버튼과 draw(stroke)버튼을 하나로 통합하였음. 이를 통해 유저가 하나의 버튼에서 두가지 드로잉 모드로 원할 때마다 전환할 수 있도록 업데이트, 그리고 fillscreen 버튼을 따로 분리하여 UI를 개선하였음.
4. modeBtn각각의 두 케이스(fill, stroke)에 대해서 isfilling = false; 으로 셋팅하여 screenfill 버튼을 누른 유저가 자연스럽게 screenfill상태를 빠져나가 드로잉 모드(fill, stroke)로 전환할 수 있도록 구현하였음. 
5. erase버튼을 클릭하고 나서 mode버튼(fill,stroke)을 클릭하여 stroke 모드로 다시 전환하려는 경우 eraser 적용후에도 strokeStyle은 지우개색인 하얀색이 아니라 기존 fillStyle과 같은 색상으로 적용해야 하므로 onModeClick에 ctx.strokeStyle = ctx.fillStyle; 추가하여 버그 해결완료.
6. 5. 경우와 유사하게 eraser버튼을 클릭하면 strokeStyle이 하얀색이 되어버려서 직후에 textstroke 클릭시 유저가 선택한 색상 적용 안되고, 하얀색이 텍스트에 적용이 되버리는 버그가 발생했었는데, onDoubleClick 함수에서 stroke 처리를 담당하는 코드의 save와 restore 사이에 ctx.strokeStyle = ctx.fillStyle; 코드 추가 적용하여 유저가 선택한 색상으로 적용되게 버그 해결완료.

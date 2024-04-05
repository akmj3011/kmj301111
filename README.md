<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>카운트다운 타이머</title>
<style>
  body {
    font-family: Arial, sans-serif;
    text-align: center;
  }

  .button-container {
    display: inline-block;
    margin-top: 50px;
  }

  .button {
    width: 120px;
    height: 50px;
    margin: 0 10px;
    background-color: #008CBA;
    color: white;
    border: none;
    border-radius: 5px;
    font-size: 18px;
    cursor: pointer;
  }

  #timer-container {
    font-size: 24px;
    margin-top: 20px;
  }
</style>
</head>
<body>
<div class="button-container">
  <button class="button" onclick="startTimer()">START</button>
  <button class="button" onclick="stopTimer()">STOP</button>
  <button class="button" onclick="resetTimer()">RESET</button>
</div>

<div id="timer-container">00:00:00</div>

<script>
  let timer;
  let totalSeconds = 0;

  function startTimer() {
    // 타이머가 이미 시작 중인 경우에는 중복 실행을 막기 위해 리턴
    if (timer) return;

    // 시작 버튼 클릭 시 타이머 시작
    timer = setInterval(() => {
      totalSeconds++;

      // 시간, 분, 초 계산
      let hours = Math.floor(totalSeconds / 3600);
      let minutes = Math.floor((totalSeconds % 3600) / 60);
      let seconds = totalSeconds % 60;

      // 시간, 분, 초를 2자리 숫자로 표시하고 시간이 99시간을 초과하지 않도록 제한
      let formattedTime = `${String(hours).padStart(2, '0')}:${String(minutes).padStart(2, '0')}:${String(seconds).padStart(2, '0')}`;
      document.getElementById('timer-container').textContent = formattedTime;
    }, 1000);
  }

  function stopTimer() {
    clearInterval(timer);
    timer = null; // 타이머를 정지하면서 변수 초기화
  }

  function resetTimer() {
    clearInterval(timer);
    timer = null; // 타이머를 정지하면서 변수 초기화
    totalSeconds = 0;
    document.getElementById('timer-container').textContent = '00:00:00';
  }
</script>
</body>
</html>

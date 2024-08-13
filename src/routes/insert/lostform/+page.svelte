<script>
</script>

<style>
    @import url('https://fonts.googleapis.com/css2?family=Pretendard:wght@400;700&display=swap');

    .container {
      width: 375px;
      height: 812px; 
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: flex-start; 
      background-color: #F3F4F6;
      font-family: 'Pretendard', sans-serif;
      margin: 0 auto;
      overflow: hidden;
      border-radius: 32px;
      padding: 20px;
      position: relative;
    }

    h1 {
      display: flex;
      align-items: center;
      padding: 16px;
      padding-top: 48px;
      font-size: 28px;
      font-weight: bold;
      width: 100%;
    }

    .input-container {
      width: 100%;
      margin-top: 16px;
    }

    label {
      display: block;
      font-size: 18px;
      margin-bottom: 10px;
    }

    input[type="text"] {
      width: 279px;
      padding: 12px;
      font-size: 16px;
      border: none;
      border-bottom: 2px solid #F59E0B; 
      outline: none;
      margin-bottom: 16px;
      background-color: transparent;
    }

    .textarea-container {
        width: 310px;
        height: 287px;
        padding: 12px;
        font-size: 16px;
        border: 1px solid #D1D5DB;
        border-radius: 8px;
        background-color: white;
        resize: none;
        margin-bottom: 16px;
        position: relative;
    }

    .textarea-content {
      width: 100%;
      height: 100%;
      border: none;
      outline: none;
      resize: none;
      background-color: transparent;
      padding-right: 40px; 
    }

    .textarea-container img {
      position: absolute;
      bottom: 12px;
      right: 12px;
      cursor: pointer;
    }

    .button {
      width: 100%;
      padding: 16px;
      font-size: 18px;
      font-weight: bold;
      color: white;
      background-color: #F59E0B; 
      border: none;
      border-radius: 8px;
      cursor: pointer;
      text-align: center;
      margin-top: 20px; 
    }
</style>

<div class="container">
    <h1>등록</h1>

    <div class="input-container">
        <label for="title">제목을 입력해주세요.</label>
        <input type="text" id="title" placeholder="ex) SRC에서 에어팟 찾았어요.">
    </div>

    <div class="input-container">
        <label for="location">어디서 잃어버렸나요?</label>
        <input type="text" id="location" placeholder="ex) SRC관">
    </div>

    <div class="input-container">
        <label for="description">세부 설명을 입력해주세요.</label>
        <div class="textarea-container">
            <textarea id="description" class="textarea-content" placeholder="내용을 입력해주세요."></textarea>
            <img src="/pic.svg" alt="이미지 추가 아이콘">
        </div>
    </div>

    <button class="button">완료하기</button>
</div>

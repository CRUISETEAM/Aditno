<script>
  import { goto } from '$app/navigation';

  function handleSubmit() {
    goto('/lost'); 
  }
</script>

<style>
  @import url('https://fonts.googleapis.com/css2?family=Pretendard:wght@400;700&display=swap');

  .container {
    width: 375px;
    height: 890px;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: flex-start;
    position: relative;
    background-color: #F3F4F6;
    font-family: 'Pretendard', sans-serif;
    margin: 0 auto;
    overflow: hidden;
    border-radius: 32px;
    margin: 40px auto 0; 
  }

  h1 {
      font-size: 28px;
      font-weight: 700;
      margin-bottom: 40px;
      width: 100%;
      text-align: left;
      margin-top: 120px;
      margin-left: 94px;
  }

  .input-container {
      width: 279px;
      margin-bottom: 30px;
  }

  label {
      display: block;
      font-size: 18px;
      font-weight: 300;
      color: #000;
      margin-bottom: 10px;
  }

  input[type="text"], textarea {
      width: 100%;
      padding: 10px 0;
      font-size: 18px;
      border: none;
      border-bottom: 3px solid #6184CA;
      outline: none;
      background-color: transparent;
      font-family: 'Pretendard', sans-serif;
  }

  input[type="text"]::placeholder,
  textarea::placeholder {
      color: #6F6F6F;
  }

  .textarea-container {
      margin-bottom: 30px;
  }

  .image-container {
      position: relative;
  }

  #image-upload {
      display: block;
      margin: 10px auto 0 auto; 
      margin-top: 30px;
      width: 80px;
      height: 90px; 
      cursor: pointer;
  }

  .button {
    width: 310px;
    height: 50px;
      font-size: 18px;
      font-weight: 700;
      color: white;
      background-color: #6184CA;
      border: none;
      border-radius: 8px;
      cursor: pointer;
      text-align: center;
      margin-top: 50px;
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
      <input type="text" id="location" placeholder="ex) SRC 도서관에서 잃어버렸어요.">
  </div>

  <div class="input-container textarea-container">
      <label for="description">세부 설명을 입력해주세요.</label>
      <textarea id="description" placeholder="내용을 입력해주세요." rows="5"></textarea>
  </div>

  <div class="input-container image-container">
      <label for="image-upload">사진을 등록해주세요.</label>
      <img src="/pic.svg" alt="이미지 등록" id="image-upload">
  </div>

  <button class="button" on:click={handleSubmit}>완료하기</button>
</div>

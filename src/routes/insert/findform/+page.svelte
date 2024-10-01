<!-- API 내용 필수요건 충족 안함. 현재 등록 안됨 -->
<script>
    // @ts-nocheck
      import axios from 'axios';
    
      function handleSubmit() {
          const title = document.getElementById('title').value;
          const description = document.getElementById('description').value;
          const time = new Date().toISOString();  
          const location = "Some default location";  
    
          
          if (!title || !description) {
              alert('모든 필드를 입력해주세요!');
              return;
          }
    
        
          const data = {
              title: title,
              location: location, 
              time: time,
              detail: description
          };
          axios.post('https://port-0-uhditknow-backend-m0z0hcc2db07a95e.sel4.cloudtype.app/got/add', data)
            .then(response => {
              console.log('Successfully submitted:', response.data);
              window.location.href = "/find";  
              
            })
            .catch(error => {
              console.error('Error submitting form:', error);
              alert('폼 제출 중 오류가 발생했습니다. 다시 시도해주세요.');
            });
      }
    
      function triggerFileUpload() {
          document.getElementById('file-input').click();
      }
    
      function handleFileChange(event) {
          const file = event.target.files[0];
          if (file) {
              const reader = new FileReader();
              reader.onload = function(e) {
                  document.getElementById('image-upload').src = e.target.result;
              };
              reader.readAsDataURL(file);
          }
      }
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
          font-weight: 500;
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
    
      /* .image-container {
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
    
      #file-input {
          display: none; 
      } */
    
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
    
      <div class="input-container textarea-container">
          <label for="description">세부 설명을 입력해주세요.</label>
          <textarea id="description" placeholder="내용을 입력해주세요." rows="5"></textarea>
      </div>
    
      <!-- <div class="input-container image-container">
          <label for="image-upload">사진을 등록해주세요.</label>
          <img src="/pic.svg" alt="이미지 등록" id="image-upload" onclick="triggerFileUpload()">
          <input type="file" id="file-input" accept="image/*" onchange="handleFileChange(event)">
      </div> -->
    
      <button class="button" on:click={handleSubmit}>완료하기</button>
    </div>
    
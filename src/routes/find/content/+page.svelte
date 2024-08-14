<script>
    const goBack = () => {
        history.back();
    };

    const navigateToPap = () => {
        window.location.href = "/find/pap"; 
    };
</script>

<style>
    .app-container {
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

    .header {
        display: flex;
        align-items: center;
        padding: 16px;
        font-size: 28px;
        font-weight: bold;
        width: 100%;
        position: absolute;
        top: 50px;
        left: 24px;
        z-index: 10;
    }

    .back-button {
        background: none;
        border: none;
        padding: 0;
        cursor: pointer;
        display: flex;
        align-items: center;
    }

    .back-button img {
        width: 18px;
        height: 18px;
        margin-right: 8px;
    }

    .notice {
        width: 100%;
        height: 350px;
        background-image: url('/appjam.svg'); 
        background-size: cover;
        background-position: center;
        margin-bottom: 20px;
        border-top-left-radius: 8px;
        border-top-right-radius: 8px;
    }

    .title {
        font-size: 26px;
        font-weight: 700;
        margin-bottom: 12px;
        margin-left: -128px;
    }

    .content {
        padding: 16px;
        flex: 1;
        overflow-y: auto;
        width: 100%;
        display: flex;
        flex-direction: column;
        align-items: center;
    }

    .content-text {
        font-size: 18px;
        line-height: 1.5;
        color: #676767;
        margin-top: -3px;
        max-width: 300px;
        text-align: left;
    }

    .button-container {
        display: flex;
        justify-content: center;
        width: 100%;
        padding: 16px;
    }

    .button {
        width: 310px;
        height: 50px;
        background-color: #6184CA;
        color: white;
        text-align: center;
        font-size: 20px;
        font-weight: 600;
        border-radius: 8px;
        cursor: pointer;
        border: none; 
        display: flex;
        justify-content: center; 
        align-items: center; 
    }
</style>

<div class="app-container">
    <div class="header">
        <button type="button" on:click={goBack} aria-label="Go back" class="back-button">
            <img src="/arrow.svg" alt="Back" />
        </button>
    </div>

    <div class="notice"></div>

    <div class="content">
        <div class="title">에어팟 주웠어요.</div>
        <div class="content-text">
            우린 오래 전부터 어쩔 수 없는 거였어 우주 속을 홀로 떠돌며 많이 외로워하다가 어느 순간 태양과 달이 겹치게 될 때면 모든 것을 이해할 수 있을 거야 하늘에선 비만 내렸어 뼈 속까지 젖었어 얼마 있다 비가 그쳤어 신 나게 내리더니 영화서도 볼 수 없는 눈보라가 불 때 너는 내가 처음 봤던 눈동자야 낮익은 거리들이 겨울처럼 반짝여도 니가 건네 주는 커피 위에 살얼음
        </div>
    </div>

    <div class="button-container">
        <button type="button" on:click={navigateToPap} class="button">
            내꺼예요
        </button>
    </div>
</div>

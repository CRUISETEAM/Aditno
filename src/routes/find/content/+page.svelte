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
        background-color: #F3F4F6;
        font-family: 'Pretendard', sans-serif;
        margin: 0 auto;
        overflow: hidden;
        border-radius: 32px;
        padding: 20px;
        position: relative;
    }

    .header {
        display: flex;
        align-items: center;
        padding: 16px;
        padding-top: 48px;
        font-size: 28px;
        font-weight: bold;
        width: 100%;
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

    .content {
        padding: 16px;
        flex: 1;
        overflow-y: auto;
        width: 100%;
    }

    .notice {
        width: 360px;
        height: 180px;
        background-image: url('/appjam.svg'); 
        background-size: cover;
        background-position: center;
        border-radius: 8px;
        margin-bottom: 20px;
    }

    .title {
        font-size: 26px;
        font-weight: 700;
        margin-bottom: 12px;
    }

    .subtitle {
        font-size: 14px;
        color: #898989;
        margin-bottom: 24px;
    }

    .content-text {
        font-size: 18px;
        line-height: 1.5;
        color: #676767;
    }

    .button-container {
        padding: 16px;
        width: 100%;
    }

    .button {
        width: 100%;
        padding: 16px 0;
        background-color: #F3A941;
        color: white;
        text-align: center;
        font-size: 20px;
        font-weight: 600;
        border-radius: 8px;
        cursor: pointer;
        border: none; 
    }
</style>

<div class="app-container">
    <div class="header">
        <button type="button" on:click={goBack} aria-label="Go back" class="back-button">
            <img src="/arrow.svg" alt="Back" />
        </button>
        이전
    </div>

    <div class="content">
        <div class="notice"></div>

        <div class="subtitle">2학년 4반 신희성</div>
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

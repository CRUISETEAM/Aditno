<script>
    import { onMount } from "svelte";

    let messages = ["src에서 봤어요", "저두여"];
    let newMessage = "";

    function sendMessage() {
        if (newMessage.trim() !== "") {
            messages = [...messages, newMessage];
            newMessage = "";
            scrollToBottom();
        }
    }

    function goBack() {
        history.back();
    }

    function scrollToBottom() {
        const messageList = document.getElementById('messageList');
        // @ts-ignore
        messageList.scrollTop = messageList.scrollHeight;
    }

    onMount(() => {
        scrollToBottom();
    });
</script>

<style>
    .app-container {
        width: 375px;
        height: 1100px;
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: space-between;
        position: relative;
        background-color: #F3F4F6;
        font-family: 'Pretendard', sans-serif;
        margin: 0 auto;
        overflow: hidden;
        border-radius: 32px;
        margin-top: 40px;
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
        width: 100%;
        display: flex;
        flex-direction: column;
        align-items: center;
        flex-grow: 1;
        overflow-y: auto;
    }

    .content-text {
        font-size: 18px;
        line-height: 1.5;
        color: #676767;
        max-width: 300px;
        text-align: left;
        margin-bottom: 12px;
    }

    .subtitle {
        font-size: 26px;
        font-weight: 700;
        margin-bottom: 12px;
        margin-left: -252px;
    }

    .chat-container {
        width: 100%;
        padding: 16px;
        display: flex;
        flex-direction: column;
        margin-bottom: 220px;
        margin-left: 74px;
    }

    .message-list {
        max-height: 150px;
        overflow-y: auto;
        padding-bottom: 10px;
    }
    .message {
        width: 130px;
        height: 38px;
        padding: 8px;
        border-radius: 25px 25px 25px 0px; 
        background-color: #6184CA;
        color: #fff;
        margin-bottom: 14px;
        max-width: 70%;
        font-size: 16px;
        display: flex; 
        align-items: center; 
        justify-content: center; 
        text-align: center; 
}

    .message-input {
        position: absolute;
        top: 50%;
        left: 50%;
        transform: translate(-50%, -50%);
        width: 320px;
        height: 40px;
        display: flex;
        align-items: center;
        margin-top: 440px;
    }

    .message-input input {
        height: 40px;
        flex: 1;
        padding: 10px;
        border: 1px solid #e5e7eb;
        border-radius: 30px;
        margin-right: 8px;
        font-size: 16px;
        color: #6184CA;
    }

    .message-input input::placeholder {
        color: #6184CA;
    }

    .message-input button {
        background: none;
        border: none;
        cursor: pointer;
        
    }

    .message-input img {
        width: 28px;
        height: 28px;
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
        <div class="subtitle">댓글</div>
    </div>

    <div class="chat-container">
        <div class="message-list" id="messageList">
            {#each messages as message}
                <div class="message">{message}</div>
            {/each}
        </div>
        <div class="message-input">
            <input type="text" bind:value={newMessage} placeholder="여기에 메시지를 입력하세요." />
            <button on:click={sendMessage}>
                <img src="/send.svg" alt="Send" />
            </button>
        </div>
    </div>
</div>

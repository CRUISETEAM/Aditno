<script>
    import { onMount } from 'svelte';
    import { goto } from '$app/navigation';

    /**
     * @type {string | null}
     */
    let selectedOption = null;

    /**
     * @param {string | null} option
     */
    function handleIconClick(option) {
        selectedOption = option;
    }

    function handleSubmit() {
        if (!selectedOption) {
            alert('이미지를 선택해 주세요.');
        } else {
            if (selectedOption === '아이') {
                goto('/insert/findform');
            } else if (selectedOption === '부모') {
                goto('/insert/lostform');
            }
        }
    }

    /**
     * @param {KeyboardEvent & { currentTarget: EventTarget & HTMLButtonElement; }} event
     * @param {string | null} option
     */
    function handleKeyDown(event, option) {
        if (event.key === 'Enter' || event.key === ' ') {
            handleIconClick(option);
        }
    }

    function goBack() {
        goto('/find');
    }

    onMount(() => {
        selectedOption = null;
    });
</script>

<style>
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

    .back-button {
        position: absolute;
        top: 20px;
        left: 20px;
        background: none;
        border: none;
        cursor: pointer;
        outline: none;
        margin-top: 50px;
        margin-left: 18px;
    }

    .back-button img {
        width: 20px;
        height: 20px;
    }

    .header {
        text-align: left;
        margin-bottom: 20px;
        width: 100%;
        padding-left: 85px;
        padding-top: 240px;
    }

    .header h2 {
        font-size: 28px;
        font-weight: 700;
        margin: 5px 0;
    }

    .header p {
        color: #898989;
        font-size: 14px;
        margin: 5px 0;
    }

    .icon-container {
        display: flex;
        align-items: center;
        margin-bottom: 40px;
    }

    .icon {
        border: none;
        background: none;
        padding: 0;
        cursor: pointer;
        display: flex;
        flex-direction: column;
        align-items: center;
        outline: none;
        margin: 0 40px;
    }

    .icon img {
        width: 100px;
        height: auto;
        margin-bottom: 10px;
        cursor: pointer;
        transition: transform 0.3s, border 0.3s;
    }

    .icon img.selected {
        transform: scale(1.1);
    }

    .icon p {
        color: #808080;
        font-size: 18px;
        font-weight: 500;
        margin: 0;
    }

    .next-button {
        width: 310px;
        height: 50px;
        background-color: #6184CA;
        border: none;
        border-radius: 8px;
        color: #FFFFFF;
        font-size: 18pt;
        font-family: 'Pretendard', sans-serif;
        font-weight: 600;
        cursor: pointer;
        position: absolute;
        bottom: 120px;
        display: flex;
        align-items: center;
        justify-content: center;
        text-decoration: none;
    }
</style>

<div class="container">
    <button class="back-button" on:click={goBack}>
        <img src="/arrow.svg" alt="뒤로 가기" />
    </button>
    <div class="header">
        <h2>등록</h2>
        <p>아래에서 등록 목록을 선택해주세요.</p>
    </div>
    <div class="icon-container">
        <button
            class="icon"
            tabindex="0"
            on:click={() => handleIconClick('아이')}
            on:keydown={(e) => handleKeyDown(e, '아이')}
        >
            <img
                src="/find.svg"
                alt="찾았다면"
                class:selected={selectedOption === '아이'}
            />
            <p>찾았다면</p>
        </button>
        <button
            class="icon"
            tabindex="0"
            on:click={() => handleIconClick('부모')}
            on:keydown={(e) => handleKeyDown(e, '부모')}
        >
            <img
                src="/lost2.svg"
                alt="잃어버렸다면"
                class:selected={selectedOption === '부모'}
            />
            <p>잃어버렸다면</p>
        </button>
    </div>
    <button class="next-button" on:click={handleSubmit}>다음으로</button>
</div>

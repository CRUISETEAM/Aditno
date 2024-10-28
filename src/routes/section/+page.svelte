<script>
    import { goto } from '$app/navigation';

    /**
     * @param {string | URL} url
     */
    function handleNavigate(url) {
        goto(url);
    }
</script>

<style>
    .container {
        display: flex; 
        justify-content: center;
        align-items: center;
        flex-wrap: wrap; 
        gap: 20px; 
        padding: 20px; 
        height: 100vh; 
    }

    .card {
        background-color: white;
        border-radius: 8px;
        padding: 20px;
        display: flex;
        align-items: center;
        justify-content: space-between;
        width: 280px;
        height: 200px;
    }

    .card-content {
        display: flex;
        flex-direction: column;
        max-width: 180px; 
    }

    .card-title {
        font-size: 32px; 
        font-weight: bold;
        margin-bottom: 8px;
        white-space: nowrap; 
    }

    .card-description {
        font-size: 20px; 
        color: #6184CA;
        margin-bottom: 16px;
        white-space: nowrap; 
        font-weight: 500;
    }

    .card img {
        width: 100px;
        height: 100px;
        margin-top: 40px; 
    }

    .navigate-button {
        font-size: 18px;
        color: #848484;
        cursor: pointer;
        display: flex;
        align-items: center;
    }

    .navigate-button::after {
        content: '→';
        margin-left: 4px;
    }
</style>

<div class="container">
    <div class="card">
        <div class="card-content">
            <div class="card-title">물건을 찾으시나요?</div>
            <div class="card-description">서비스에 있는<br>분실물을<br> 확인해보세요.</div>
            <!-- svelte-ignore a11y-no-static-element-interactions -->
            <!-- svelte-ignore a11y-click-events-have-key-events -->
            <div class="navigate-button" on:click={() => handleNavigate('/find')}>이동하기</div>
        </div>
        <img src="section1.svg" alt="Emoji1" loading="lazy">
    </div>

    <div class="card">
        <div class="card-content">
            <div class="card-title">물건을 잃어버렸나요?</div>
            <div class="card-description">잃어버린 물건을<br> 서비스에 <br>등록해봐요!</div>
            <!-- svelte-ignore a11y-no-static-element-interactions -->
            <!-- svelte-ignore a11y-click-events-have-key-events -->
            <div class="navigate-button" on:click={() => handleNavigate('/lost')}>이동하기</div>
        </div>
        <img src="section2.svg" alt="Emoji2" loading="lazy"> 
    </div>
</div>

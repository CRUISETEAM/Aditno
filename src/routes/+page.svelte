<script>
    import { goto } from '$app/navigation';

    function handleSignupClick() {
        goto('section'); 
    }
</script>

<style>
    .container {
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: center;
        height: 100vh; 
        position: relative;
    }

    .logo {
        width: 140px;
        height: auto;
        margin-bottom: 20px; /* 로고와 버튼 사이의 간격 */
    }

    .signup-button {
        width: 310px;
        height: 60px;
        background-color: #6184CA;
        border: none;
        border-radius: 8px;
        color: #FFFFFF;
        font-size: 18pt;
        font-family: 'Pretendard', sans-serif;
        font-weight: 600;
        cursor: pointer;
        display: flex;
        align-items: center;
        justify-content: center;
        margin-top: 70px; 
    }
</style>

<div class="container"> 
    <img src="/logo.svg" alt="Logo" class="logo">
    <button class="signup-button" on:click={handleSignupClick}>
        회원가입
    </button>
</div>

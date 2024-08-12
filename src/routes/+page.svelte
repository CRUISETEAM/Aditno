<script>
    import { goto } from '$app/navigation';

    function handleSignupClick() {
        goto('find'); 
    }
</script>

<style>
.container {
    width: 375px;
    height: 812px;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    position: relative;
    background-color: #F3F4F6;
    font-family: 'Pretendard', sans-serif;
    margin: 0 auto;
    overflow: hidden;
    border-radius: 32px;
}

.logo {
    width: 140px;
    height: auto;
    position: absolute;
    top: 350px;
}

.signup-button {
    width: 310px;
    height: 50px;
    background-color: #F3A941;
    border: none;
    border-radius: 8px;
    color: #FFFFFF;
    font-size: 18pt;
    font-family: 'Pretendard', sans-serif;
    font-weight: 600;
    cursor: pointer;
    position: absolute;
    bottom: 100px;
    display: flex;
    align-items: center;
    justify-content: center;
}

.signup-button:hover {
    background-color: #f0bb71;
}

.footer {
    position: absolute;
    bottom: 60px;
    font-size: 14px;
    color: #808080;
}
</style>

<div class="container"> 
    <img src="/logo.svg" alt="Logo" class="logo">
    <button class="signup-button" on:click={handleSignupClick}>
        회원가입
    </button>
    <div class="footer">©CRUISE</div> 
</div>



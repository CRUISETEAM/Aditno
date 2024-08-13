<script>
    import { goto } from '$app/navigation';
    import { page } from '$app/stores';
    import { get } from 'svelte/store';

    // @ts-ignore
    const isActive = (path) => {
        const currentPage = get(page);
        return currentPage.url.pathname === path;
    };

    const navItems = [
        { icon: 'found.svg', label: '찾았어요', link: '/find' },
        { icon: 'lost.svg', label: '잃어버렸어요', link: '/lost' },
        { icon: 'here.svg', label: '여기있어요', link: '/here' },
        { icon: 'register.svg', label: '물품 등록', link: '/insert/choose' }
    ];

    // @ts-ignore
    const handleItemClick = (event, link) => {
        event.preventDefault(); 
        goto(link);
    };
</script>

<style>
    .container {
        width: 375px;
        height: 890px; 
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
        text-align: left;
        width: 100%;
        margin-bottom: 20px;
        padding-top: 60px;
        font-size: 28px;
        font-weight: 700;
        padding-left: 42px;
    }
    .header p {
        color: #898989;
        font-size: 14px;
        margin: 8px 0;
        font-weight: 200;
    }

    .notice {
        width: 330px;
        height: 174px;
        background-image: url('appjam.svg');
        background-size: cover;
        background-position: center;
        border-radius: 8px;
        margin-bottom: 20px;
    }

    .list-item {
        display: flex;
        align-items: center;
        background-color: #F3F4F6;
        padding: 0 16px;
        border-radius: 8px;
        margin-bottom: 8px;
        width: 328px;
        height: 90px;
        text-decoration: none;
        color: inherit;
        cursor: pointer;
        position: relative; 
    }

    .list-item:not(:last-child)::after {
        content: '';
        position: absolute;
        bottom: -4px; 
        left: 16px;
        width: 296px;
        height: 1px;
        background-color: #DCDCDC;
    }

    .list-item:last-child::after {
        content: none;
    }

    .item-image {
        width: 70px;
        height: 70px;
        border-radius: 8px;
        margin-right: 12px;
    }

    .item-content {
        display: flex;
        flex-direction: column;
    }

    .item-title {
        font-size: 20px;
        font-weight: 600;
        margin-bottom: 2px;
    }

    .item-subtitle {
        font-size: 14px;
        color: #898989;
    }

    .navbar {
        display: flex;
        justify-content: space-around;
        align-items: center;
        background-color: #F3F4F6;
        padding: 10px 0;
        width: 100%;
        max-width: 375px;
        position: fixed;
        bottom: 10px; 
        left: 50%;
        transform: translateX(-50%);
        border-radius: 0 0 32px 32px;
    }

    .navbar-item {
        display: flex;
        flex-direction: column;
        align-items: center;
        text-decoration: none;
        font-size: 12px;
    }

    .navbar-item img {
        width: 30px;
        height: 30px;
        margin-bottom: 2px;
        filter: grayscale(100%); 
    }

    .navbar-item.active img {
        filter: none; 
    }

    .navbar-item.active span {
        color: #FF6F00; 
    }

    .navbar-item span {
        color: #333;
    }
</style>

<div class="container">
    <div class="header">
        찾았어요
        <p>잃어버린 물건이 있는지 확인해보세요.</p> 
    </div>
    <div class="notice"></div>
    
    <a class="list-item" href="/find/content" on:click={(event) => handleItemClick(event, '/find/content')}>
        <img src="appjam.svg" alt="" class="item-image">
        <div class="item-content">
            <div class="item-title">에어팟 주웠어요.</div>
            <div class="item-subtitle">2학년 4반 신희성</div>
        </div>
    </a>

    <a class="list-item" href="/find/content" on:click={(event) => handleItemClick(event, '/find/content')}>
        <img src="appjam.svg" alt="" class="item-image">
        <div class="item-content">
            <div class="item-title">에어팟 주웠어요.</div>
            <div class="item-subtitle">2학년 4반 신희성</div>
        </div>
    </a>

    <a class="list-item" href="/find/content" on:click={(event) => handleItemClick(event, '/find/content')}>
        <img src="appjam.svg" alt="" class="item-image">
        <div class="item-content">
            <div class="item-title">에어팟 주웠어요.</div>
            <div class="item-subtitle">2학년 4반 신희성</div>
        </div>
    </a>

    <a class="list-item" href="/find/content" on:click={(event) => handleItemClick(event, '/find/content')}>
        <img src="appjam.svg" alt="" class="item-image">
        <div class="item-content">
            <div class="item-title">에어팟 주웠어요.</div>
            <div class="item-subtitle">2학년 4반 신희성</div>
        </div>
    </a>

    <div class="spacer"></div>
</div>

<nav class="navbar">
    {#each navItems as item}
        <a class="navbar-item {isActive(item.link) ? 'active' : ''}" href={item.link}>
            <img src={item.icon} alt={item.label} />
            <span>{item.label}</span>
        </a>
    {/each}
</nav>

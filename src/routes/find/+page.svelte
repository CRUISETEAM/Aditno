<script>
    import axios from 'axios';
    import { goto } from '$app/navigation';
    import { onMount } from 'svelte';

    let currentTab = 'lost';
    // @ts-ignore
    /**
   * @type {any[]}
   */
    let listData = []; 

    const navItems = [
        { label: '찾았어요', id: 'find', path: '/find' },
        { label: '잃어버렸어요', id: 'lost', path: '/lost' },
    ];

    const handleTabClick = (/** @type {string} */ tabId) => {
        const selectedItem = navItems.find(item => item.id === tabId);
        if (selectedItem) {
            currentTab = tabId;  
            goto(selectedItem.path);  
        }
    };

    const handleItemClick = (/** @type {MouseEvent & { currentTarget: EventTarget & HTMLAnchorElement; }} */ event, /** @type {string | URL} */ link) => {
        event.preventDefault(); 
        goto(link);
    };

    const fetchData = async () => {
        try {
            const response = await axios.get('https://port-0-uhditknow-backend-m0z0hcc2db07a95e.sel4.cloudtype.app/got');
            listData = response.data; 
        } catch (error) {
            console.error('Error fetching data:', error);
        }
    };

    onMount(() => {
        fetchData();
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
        margin: 30px auto 0;
        overflow: hidden;
        border-radius: 32px;
        padding-top: 20px; 
    }

    .header {
        text-align: left;
        width: 100%;
        margin-bottom: 15px; 
        font-size: 28px;
        font-weight: 700;
        padding-left: 42px;
        margin-top: 70px;
        margin-left: 30px;
    }

    .tabs {
        display: flex;
        justify-content: flex-start; 
        width: 180px; 
        margin-bottom: 10px;
        padding-left: 42px; 
        margin-left: -160px;
    }

    .tab-item {
    padding: 10px 0;
    text-align: left;
    font-size: 22px;
    cursor: pointer;
    border: none; 
    outline: none;
    border-bottom: 2px solid transparent;
    margin-right: 16px; 
    white-space: nowrap; 
    color: #808080; 
    background: none;
}


    .tab-item.active {
        border-bottom: 4px solid #6184CA;
        font-weight: 700;
        color: #6184CA; 
    }

    .register-button {
        display: flex;
        align-items: center;
        margin-top: 20px;
        margin-right: 200px;
        margin-bottom: 15px; 
        color: #6184CA;
        cursor: pointer;
        text-decoration: none;
        font-size: 18px;
    }

    .register-button img {
        margin-right: 8px;
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
        margin-top: 20px;
        margin-left: 30px;
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
</style>

<div class="container">
    <div class="header">홈</div>

    <div class="tabs">
        {#each navItems as item}
            <button 
                type="button"
                class="tab-item {currentTab === item.id ? 'active' : ''}" 
                on:click={() => handleTabClick(item.id)}
                on:keydown={(event) => {
                    if (event.key === 'Enter' || event.key === ' ') handleTabClick(item.id);
                }}
                role="tab" 
                aria-selected="{currentTab === item.id}"
            >
                {item.label}
            </button>
        {/each}
    </div>

    <a class="register-button" href="/insert/choose" on:click={(event) => handleItemClick(event, '/insert/choose')}>
        <img src="pencil.svg" alt="Pencil Icon" />
        등록하기
    </a>

    {#each listData as item}
        <a class="list-item" href="/find/content" on:click={(event) => handleItemClick(event, '/lost/content')}>
            <img src="{item.image}" alt="{item.title}" class="item-image">
            <div class="item-content">
                <div class="item-title">{item.title}</div>
                <div class="item-subtitle">{item.subtitle}</div>
            </div>
        </a>
    {/each}
</div>

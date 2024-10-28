<script>
    import axios from 'axios';
    import { goto } from '$app/navigation';
    import { onMount } from 'svelte';

    let currentTab = 'lost';
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
        display: flex;
        flex-direction: column;
        align-items: center; /* 중앙 정렬 */
        padding: 20px;
    }

    .header {
        width: 100%;
        margin-bottom: 15px; 
        font-size: 28px;
        font-weight: 700;
        text-align: left;
        padding-left: 30px; /* 왼쪽에서 30px 이동 */
    }

    .tabs {
        display: flex;
        justify-content: center; /* 중앙 정렬 */
        width: 100%;
        margin-bottom: 10px;
    }

    .tab-item {
        padding: 10px 16px;
        font-size: 22px;
        cursor: pointer;
        border: none; 
        outline: none;
        border-bottom: 2px solid transparent;
        margin: 0 8px; 
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
        margin: 20px 0;
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
        padding: 16px;
        border-radius: 8px;
        margin: 10px 0;
        width: 100%; /* 전체 폭 사용 */
        max-width: 400px; /* 최대 폭 설정 */
        text-decoration: none;
        color: inherit;
        background-color: transparent; /* 배경색 제거 */
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
        <a class="list-item" href={`/find/content/${item.id}`} on:click={(event) => handleItemClick(event, `/find/content/${item.id}`)}>
            <img src="{item.image}" alt="{item.title}" class="item-image">
            <div class="item-content">
                <div class="item-title">{item.title}</div>
                <div class="item-subtitle">{item.subtitle}</div>
            </div>
        </a>
    {/each}
</div>

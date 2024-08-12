<script>
    const navItems = [
        { icon: '/found.svg', label: '찾았어요', link: '/found' },
        { icon: '/lost.svg', label: '잃어버렸어요', link: '/lost' },
        { icon: '/here.svg', label: '여기있어요', link: '/here' },
        { icon: '/register.svg', label: '물품 등록', link: '/register' }
    ];
</script>

<style>
    .navbar {
        display: flex;
        justify-content: space-around;
        align-items: center;
        background-color: #f9f9f9;
        padding: 10px 0;
        border-top: 1px solid #ccc;
        border-bottom: 1px solid #ccc;
        width: 100%;
        max-width: 375px;
        position: fixed;
        bottom: 0;
        left: 50%;
        transform: translateX(-50%);
        border-radius: 0 0 32px 32px;
    }

    .navbar-item {
        display: flex;
        flex-direction: column;
        align-items: center;
        text-decoration: none;
        color: #333;
        font-size: 12px;
    }

    .navbar-item img {
        width: 30px;
        height: 30px;
        margin-bottom: 2px;
    }
</style>

<nav class="navbar">
    {#each navItems as item}
        <a class="navbar-item" href={item.link}>
            <img src={item.icon} alt={item.label} />
            <span>{item.label}</span>
        </a>
    {/each}
</nav>

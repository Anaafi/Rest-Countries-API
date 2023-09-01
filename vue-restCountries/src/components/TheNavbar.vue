<script scope>

</script>

<template>
    <main>
        <h3>Where in the world?</h3>
        <div class="nav-items">
            <img src="../assets/Group3.svg">
            <p>Dark Mode</p>
        </div>
    </main>
    
</template>

<style scoped>
main{
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 30px 16px;
}
.nav-items{
    display: flex;
    align-items: center;
    gap: 8px;
}

main h3{
    color: #111517;
    font-family: 'Nunito Sans';
    font-size: 14px;
    font-style: normal;
    font-weight: 800;
    line-height: 20px; 
}
.nav-items img{
    width: 16px;
    height: 16px;
}
.nav-items p{
    color: #111517;
    font-family: 'Nunito Sans';
    font-size: 12px;
    font-style: normal;
    font-weight: 600;
    line-height: normal;
}

@media (min-width: 1024px) {
    main{
        padding: 24px 80px;
    }

    main h3{
        line-height: normal;
        font-size: 24px;
    }
    .nav-items p{
        font-size: 16px;
    }
    .nav-items img{
    width: 20px;
    height: 20px;
}

}
</style>
<template>
    <div class="footer">
        <div class="footer-principal">
            <div class="social">
                <p>Reach me at</p>
                <div class="social-icons">
                    <a href="https://www.facebook.com/"><i class="fab fa-facebook-f"></i></a>
                    <a href="https://www.instagram.com/"><i class="fab fa-instagram"></i></a>
                    <a href="https://www.twitter.com/"><i class="fab fa-twitter"></i></a>
                    <a href="https://www.linkedin.com/"><i class="fab fa-linkedin-in"></i></a>
                </div>

            </div>
            <div class="sitemap">
                <a href="#">Home</a>
                <a href="#">About</a>
                <a href="#">Contact</a>
            </div>
        </div>
        <div class="legal">
            <p>© {{ date.getFullYear() }} Task Tracker. All rights reserved.</p>
        </div>
    </div>
</template>

<script>
export default {
    name: "Footer",
    data() {
        date: Date()
    },
    created() {
        console.log('footer created')
        this.date = new Date()
    },
    methods: {}
}
</script>

<style>
.footer,
.footer-principal,
.legal {
    display: flex;
    justify-content: center;
    align-items: center;
    width: 100%;
}

.footer {
    flex-direction: column;
    background-color: #333;
    margin-top: 40px;
    color: white
}

.legal {
    margin: 20px 0 40px 0;
}

.footer-principal {
    justify-content: space-between;
    padding: 0 150px;
    width: 100%;
    margin: 20px 0;
}
.social{
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
}
.social-icons a {
    text-align: center;
    align-items: center;
    justify-content: center;
    width: 40px;
    height: 40px;
    font-size: 28px;
    margin: 30px 10px 0 10px;
    transition: all ease .5s;
}
a:hover{
    color: white;
    background-color: transparent;
    text-decoration: none;
}
a i{
    transition: all ease .5s;
}
a:hover i{
    transform: scale(1.3,1.3);
}
</style>
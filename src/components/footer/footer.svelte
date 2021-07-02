<script>
     let date = new Date();
     let year = date.getFullYear();
</script>
<footer>
        <div class="copyright">
            <p>Copyright &copy {year} Aniruddha Ghosh</p>
            <p>The website code is an open source and it's code is published in
            <br>
            <a href="https://github.com/AGhosh2020/The-Random-Password-Generator"><img src="img/github.png" alt="GitHub"></a></p>
        </div>
     
    </footer>
<style>
     footer{
        padding: 40px;
        text-align: center;
    }
    .copyright{
        font-size:14px;
        display: inline-block;
        padding:20px;
        border-top:1px solid #ddd;
    }
    img{
        width:47px;
        height:19px;
        filter: invert(100%);
    }
    :global(body.dark) img{
        filter: invert(0%);
    }
</style>
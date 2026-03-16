<script>
</script>

<nav class="menu">
<a href="/">Home</a>
<a href="/products">Products</a>
<a href="/contact">Contact</a>
<a href="/configurator">configurateur </a>
</nav>

<main>
<slot />
</main>

<style>
.menu{
display:flex;
gap:20px;
background:#222;
padding:15px;
}

.menu a{
color:white;
text-decoration:none;
font-weight:bold;
}

.menu a:hover{
color:#ff6600;
}
</style>
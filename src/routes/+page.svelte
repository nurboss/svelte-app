<script>
  import "./app.css";
</script>

<svelte:head>
<title>Home</title>
<meta name="description" content="Svelte jobtask" />
</svelte:head>

<section>
<div class="min-h-screen">
    <div class="min-h-screen grid grid-cols-4 md:grid-cols-12 grid-rows-6 grid-flow-col-dense">
      <div class="hidden md:block col-span-4 row-span-3 md:col-span-2 md:row-span-3 bg-blue-400"><div></div></div>

      <div class="hidden md:block col-span-4 row-span-3 md:col-span-2 md:row-span-2 bg-teal-400"><div></div></div>

      <div class="hidden md:block col-span-4 row-span-3 md:col-span-6 md:row-span-1 bg-fuchsia-400 "><div></div></div>

      <div class="col-span-4 row-span-3 md:col-span-4 md:row-span-5 bg-rose-100 "><div></div></div>

      <div class="hidden md:block col-span-4 row-span-3  md:col-span-6 md:row-span-2 bg-blue-400"><div></div></div>

      <div class="col-span-4 row-span-3 md:col-span-4 md:row-span-4 bg-yellow-100 ">
        <div class="w-full h-full flex justify-center items-center">
        <div class="box">
          <div class="circle">
            <div class="big_mouten"></div>
            <div class="small_mounten"></div>
          </div>
        </div>

      </div></div>

      <div class="hidden md:block col-span-4 row-span-3 md:col-span-2 md:row-span-4 bg-emerald-400 "><div></div></div>
      
    </div>
  
  </div>
</section>

<style>
.box{
  width: 300px;
  height: 300px;
  background: #293462;
  display: flex;
  justify-content: center;
  align-items: center;

}
.circle{
  width: 200px;
  height: 200px;
  border-radius: 50%;
  background: #fff1c1;
  position: relative;
  overflow: hidden;
 
}
.big_mouten{
  width: 0px;
  height: 0px;
  border-bottom: 200px solid #fe5f55;
  border-right: 200px solid transparent;
  border-left: 200px solid transparent;
  position: absolute;
  top: 64px;
  left: -57px;
}
.small_mounten{
  width: 0px;
  height: 0px;
  border-bottom: 100px solid #fe5f55;
  border-right: 100px solid transparent;
  border-left: 100px solid transparent;
  position: absolute;
  top: 132px;
  left: -64px;
}

</style>

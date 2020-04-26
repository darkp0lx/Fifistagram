<script>
  import {onMount} from "svelte";
  import Header from '../components/Header.svelte'
  import Main from '../components/Main.svelte'
  import SideBar from '../components/SideBar.svelte'
  import TimeLine from '../components/TimeLine.svelte'
  let data={
    }
  const API = 'https://us-central1-pugstagram-co.cloudfunctions.net/data';
  onMount(async()=>{
    const responsive= await fetch(API);
    data= await responsive.json();
  })
</script>

<div class="main">
<Header/>
<Main>
  <TimeLine  posts={data.posts}/>
  <SideBar {...data.user}/>  
</Main>

</div>

<style>
    :global(body) {
    background-color: #fafafa;
    color: rgba(38, 38, 38, 0.7);
    font-family: "Lato", sans-serif;
    margin: 0;
    padding: 0;
  }
  :global(h1, h2, h3) {
    margin: 0;
    padding: 0;
  }
</style>
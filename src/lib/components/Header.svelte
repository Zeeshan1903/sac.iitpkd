<script>
  import { goto } from '$app/navigation';
</script>

<div style="display: flex; align-items: center; justify-content: space-between; width: 100%; padding: 10px;  padding-inline: 3rem">
  <div style="display: flex; align-items: center;">
    <img src="/SACLogo.svg" alt="SAC logo" style="width:94px; height: 111px; margin-right: 10px;" />
    <img src="/SACTagline.svg" alt="SAC Tagline" style="width:291; height: 39px;" />
  </div>

  <div class="Center text-[1.3rem]" style="display: flex; gap: 4rem;">
    <button class="navButton">Home</button>
    <button class="navButton">About Us</button>
    <button class="navButton">Council</button>
    <button class="navButton">Announcements</button>
  </div>


  <div>
    <button class="Signin" on:click={() => goto('/login')} >Sign in</button>
  </div>
</div>
<style>
	:global(*){
		/* background-color: white; */
		color: rgba(54, 56, 78, 1);

	}
	.navButton{
		border: none;
	}
	.Signin{
		background-color: rgba(243, 130, 33, 1);
		width:117px ;
		height:42px;
		border-radius: 12px;
	}


</style>

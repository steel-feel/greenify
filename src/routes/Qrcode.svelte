<script>
    let imgSrc, bLoading = true;

    let sUrl = "https://api.qrserver.com/v1/create-qr-code/?size=250x250&format=svg&data=" + window.sAccountNo ;

   fetch(sUrl)
  .then(response => response.blob())
  .then(images => {
      // Then create a local URL for that image and print it 
      imgSrc = URL.createObjectURL(images)

      bLoading = false;

    
  })
</script>


<div  class="p-5 text-center relative top-15" >
{#if bLoading}
    <div class="bouncingLoader py-15"></div>
{:else}
    <img src="{imgSrc}" alt="Account QR Code">
{/if}

<h3>Show QR code to any Green Token Rewards POS or Agent for points</h3>

<img class="max-w-3/4 h-64" src="./images/qr-illus.jpg" alt="">
<br>
    <div class="p-10">

        <a href="/#/" class="no-underline cursor-pointer max-w-lg  py-2 px-16  bg-red-600 hover:bg-red-700 focus:ring-red-500 focus:ring-offset-red-200 text-white w-full transition ease-in duration-200 text-center text-base font-semibold shadow-md focus:outline-none focus:ring-2 focus:ring-offset-2  rounded-lg "
        >
           Back
    </a>

    </div>
   

</div>


<style>
    .bouncingLoader > div, .bouncingLoader:before, .bouncingLoader:after {
        display: inline-block;
        width: 13px;
        height: 13px;
        background: hsl(243, 80%, 62%);
        margin-bottom: -5px;
        border-radius: 50%;
        animation: bouncing-loader 0.6s infinite alternate;
    }
    
    .bouncingLoader > div, .bouncingLoader:before, .bouncingLoader:after {
        content: "";
    }
    
    .bouncingLoader > div {
        margin: 0 5px;
    }
    
    .bouncingLoader > div {
        animation-delay: 0.2s;
    }
    
    .bouncingLoader:after {
        animation-delay: 0.4s;
    }
    
    @keyframes bouncing-loader {
        to {
            opacity: 0.1;
            transform: translate3d(0, -16px, 0);
        }
    }
    
    
    </style>
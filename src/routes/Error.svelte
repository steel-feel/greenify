<script>
export let params = {}

let errors = [

    "This App is currently optimized for mobile. Please use mobile browser."

]

let message = errors[+(params.msg)];


</script>
<main class="bg-white relative overflow-hidden h-screen relative bg-error">
    <div class="container mx-auto h-screen pt-32 md:pt-0 px-6 z-10 flex items-center justify-between">
        <div class="container mx-auto px-6 flex flex-col-reverse lg:flex-row justify-between items-center relative">
            <div class="w-full mb-16 md:mb-8 text-center lg:text-left">
                <h1 class="font-light font-sans text-center lg:text-left text-5xl lg:text-8xl mt-12 md:mt-0 text-gray-700">
                  {message}
                </h1>
               
            </div>
             <!-- <div class="relative right-15 w-full mx-auto md:mt-0 relative max-w-md lg:max-w-2xl">
                <img src="./images/8.svg"/>
            </div>  -->
        </div>
    </div>
</main>
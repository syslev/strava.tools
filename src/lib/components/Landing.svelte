<script lang="ts">
	import * as Card from '$lib/components/ui/card';
	import Button from '$lib/components/ui/button/button.svelte';
	import * as Alert from '$lib/components/ui/alert'; // @ts-expect-error: this import does exist
	import { signIn } from '@auth/sveltekit/client';
	import '$lib/components/sidebar/svg-styles.css';

	export let sessionExpired: boolean = false;
</script>
<div class="flex flex-col justify-center items-center w-full">
    <div class="flex flex-col items-center justify-center px-4 pt-24 select-none ">
        <h1 class="z-10 text-6xl md:text-[5rem] font-bold">strava.tools</h1>
        <h2 class="z-10 font-bold text-3xl text-center">Insights&nbsp;&&nbsp;Visuals for&nbsp;Strava</h2>
        <h2 class="z-10 opacity-20 text-md md:pt-1 text-center">Not affiliated with Strava, Inc.</h2>
        <svg
            class="-mt-[180px] text-card dark:text-border"
            xmlns="http://www.w3.org/2000/svg"
            fill-rule="evenodd"
            width="250px"
            height="250px"
            viewBox="0 0 1350 1350"
            ><path
                d="M651.2 421.7 464.8 791.4l-39.4 79.2-.6 2.4 73.7-.2 73.7-.3 51.4-98.4 51.7-98.8c.2-.2 23.6 44.1 52 98.4l51.5 98.8 74.2.3 74.2.2-.6-2.3c-1.1-4.6-249.5-495.2-250.8-495.5-.8-.1-9.7 16.7-24.6 46.5"
                fill="currentColor"
            /><path
                d="m671.4 7.5-1.4 4-2.4 6.8a6003 6003 0 0 0-25 67.7L618 152.5a2038 2038 0 0 0-15.4 42.2l-.7 2.2-4.7.6a534 534 0 0 0-63 15.7 343 343 0 0 0-41.4 14.4 268 268 0 0 0-28.9 12.7 531 531 0 0 0-42.4 23.2 487 487 0 0 0-63.1 46l-13.7 12.9A517 517 0 0 0 287 387a584 584 0 0 0-25.3 38.4c-8.6 11.4-30.3 56.4-38.7 80.1-1.5 4.4-3.5 9.6-4.4 11.6s-1.7 4.7-2 6-1.8 6.7-3.4 11.9a380 380 0 0 0-10.2 39l-2.4 13.3-1.3 6.9 2.9-.6c1.6-.3 6.3-2 10.4-3.6s8.1-3 8.8-3 5-1.6 9.6-3.5 9-3.5 9.5-3.5c1 0 6.3-2 15-5.5a367 367 0 0 0 22.5-8l14.1-5.1c1-.4 2.4-3.4 3.7-7.7 22.6-79.3 87.7-164.8 161-211.5l14-9c3.7-2.3 7-4.2 7.5-4.2s2-.8 3.5-1.9 6.3-3.6 10.7-5.8a375 375 0 0 1 94-34.1A368 368 0 0 1 612 282l19.5-2.7c6-.8 18.5-1.9 27.7-2.3s17-1 17.3-1.2.2-61.6-.2-136.2L675.7 4h-1.4c-.8 0-2 1.6-2.9 3.5m85 194.7c.3 1.6 2 6.3 3.6 10.4s3 8.1 3 8.8 1.6 5 3.5 9.6 3.5 9 3.5 9.5c0 1 2 6.3 5.5 15a367 367 0 0 0 8 22.5l5.1 14.1c.5 1.5 5.1 3.4 10.7 4.4 1 .3 5.3 1.8 9.4 3.5s8 3 8.7 3 3 1 5.1 2 6.3 3 9.2 4a475 475 0 0 1 47.3 24l9.5 6a156 156 0 0 1 20.5 14 428 428 0 0 1 100.2 106l7.4 12c1.6 2.4 3.6 5.8 4.4 7.5l6.8 12.4c2.9 5.2 5.2 9.8 5.2 10.4s1.3 3.5 3 6.6a254 254 0 0 1 11.5 27.6c1.8 5 4 10.7 5 12.8s1.3 3.7 1 3.7.7 3.3 2 7.3a459 459 0 0 1 12.4 52.7l2.7 19.5c.8 6 1.9 18.5 2.3 27.7s1 17 1.2 17.3 61.4.2 135.7-.2l135.3-.6-.3-1.6c-.3-1.5-5.7-3.8-23.3-10l-35.3-13-27.8-10.1a269 269 0 0 0-17.9-6.9L1213 624l-24.5-9c-36.6-13-36-12.8-36.9-18.2a593 593 0 0 0-24.5-91.8c-18.5-51.9-57-115.6-92.1-152.5l-12.3-13A550 550 0 0 0 963 287a584 584 0 0 0-38.4-25.3c-11.4-8.6-56.4-30.3-80.1-38.7-4.4-1.5-9.6-3.5-11.6-4.4s-4.7-1.7-6-2-6.7-1.8-11.9-3.4a380 380 0 0 0-39-10.2l-13.3-2.4-6.9-1.3zM98.7 673.8l-94.8.2.3 1.7c.2 1 2.1 2.4 4.3 3.2l10 3.7L86 707.5l66.5 24.5a2038 2038 0 0 0 42.2 15.4l2.2.7.6 4.7a552 552 0 0 0 15.7 63 343 343 0 0 0 14.4 41.4 268 268 0 0 0 12.7 28.9 531 531 0 0 0 23.2 42.4 487 487 0 0 0 46 63.1l12.9 13.7A517 517 0 0 0 387 1063a584 584 0 0 0 38.4 25.3c11.4 8.6 56.4 30.3 80.1 38.7 4.4 1.5 9.6 3.5 11.6 4.4s4.7 1.7 6 2 6.7 1.8 11.9 3.4a380 380 0 0 0 39 10.2l13.3 2.4 6.9 1.3-.6-2.9c-.3-1.6-2-6.3-3.6-10.4s-3-8.1-3-8.8-1.6-5-3.5-9.6-3.5-9-3.5-9.5c0-1-2-6.3-5.5-15a367 367 0 0 0-8-22.5l-5.1-14.1c-.5-1.5-5.1-3.4-10.7-4.5-1-.2-5.3-1.7-9.4-3.4s-8-3-8.7-3-3-1-5.1-2-6.3-3-9.2-4a475 475 0 0 1-47.3-24c-.3-.3-4.5-3-9.5-6s-10.1-6.2-11.5-7.4-5.4-4.2-9-6.6a428 428 0 0 1-95-98 451 451 0 0 1-29.6-51.3 46 46 0 0 0-3-6.7C294.7 804.7 277 731 277 688.4c0-5-.3-10.6-.6-12.3l-.6-3.1-41.2.2zm1042.4 85-11 3.8c-2.5.8-7.9 2.7-12 4.4s-8 3-8.6 3.1c-.9 0-6.2 2-14.9 5.5a367 367 0 0 0-22.5 8l-14.1 5.1c-1.5.5-3.4 5.1-4.5 10.7-.2 1-1.7 5.3-3.4 9.4s-3 8-3 8.7-1 3-2 5.1-3 6.3-4 9.2a475 475 0 0 1-24 47.3l-6 9.5a156 156 0 0 1-14 20.5 428 428 0 0 1-106 100.2l-12 7.4a75 75 0 0 1-7.5 4.4l-12.4 6.8c-5.2 2.9-9.8 5.2-10.4 5.2s-3.5 1.3-6.6 3a254 254 0 0 1-27.6 11.5c-5 1.8-10.7 4-12.7 5s-3.8 1.3-3.8 1-3.3.7-7.2 2c-9.8 3.4-42.3 11-52.8 12.4l-19.5 2.7c-6 .8-18.5 1.9-27.7 2.3s-17 1-17.3 1.2-.2 61.4.2 135.7l.6 135.3 1.6-.3c1.5-.3 3.8-5.7 10-23.3l13-35.3 10.1-27.8a269 269 0 0 0 6.9-17.9l10-27.6 9-24.5a733 733 0 0 1 12.9-34.3l1-1.9 6.3-1a505 505 0 0 0 60.6-14.5 343 343 0 0 0 41.4-14.4 268 268 0 0 0 28.9-12.7 531 531 0 0 0 42.4-23.2c28.4-15.7 72.7-52.4 102.1-84.6 15.6-17.1 15.2-16.5 29-34.9a480 480 0 0 0 58.3-100l5.6-13a553 553 0 0 0 24.5-84l2.5-12.8c.6-1.8-2.2-1.4-9.5 1.4"
                fill="currentColor"
            /></svg
        >
    </div>
    <div class="flex flex-col justify-center pt-6 px-5 max-w-[575px]">
        <Card.Root>
            <Card.Header>
                {#if sessionExpired}
                    <p>
                        Your Strava session has expired. Please re-authorize your account to import your activities.
                    </p>
                {:else}
                    <p>
                        To use strava.tools, you will first need to <b
                            >import your activities from Strava.</b
                        > Click below to be taken to Strava's authorization page.
                    </p>
                {/if}
            </Card.Header>
            <Card.Content>
                <Button
                    class="bg-[#FC4C02] hover:bg-[#d14002] flex items-center mx-auto px-0 h-10 "
                    on:click={() => signIn('strava')}
                >
                    <img src="img/icon/connect_with_strava.svg" alt="Connect with Strava" class="h-14" />
                </Button>
            </Card.Content>
            <Card.Footer>
                <Alert.Root>
                    <svg
                        xmlns="http://www.w3.org/2000/svg"
                        viewBox="0 0 512 512"
                        aria-label="shield"
                        class="svg-icon h-4 w-4 inline"
                    >
                        <path
                            d="M256 0c4.6 0 9.2 1 13.4 2.9L457.7 82.8c22 9.3 38.4 31 38.3 57.2c-.5 99.2-41.3 280.7-213.6 363.2c-16.7 8-36.1 8-52.8 0C57.3 420.7 16.5 239.2 16 140c-.1-26.2 16.3-47.9 38.3-57.2L242.7 2.9C246.8 1 251.4 0 256 0zm0 66.8V444.8C394 378 431.1 230.1 432 141.4L256 66.8l0 0z"
                        />
                    </svg>
                    <Alert.Title><b class="font-large">Worried about privacy?</b></Alert.Title>
                    <Alert.Description>
                        <p>
                            This app doesn't store any of your data, full stop. We are committed to upholding the
                            highest privacy standard possible--if you want to know more, read our privacy assurance <a
                                href="https://aes.rip/privacy/"
                                target="_blank"
                                rel="noopener noreferrer">here</a
                            >.
                        </p>
                        <p>
                            This app is <a
                                href="https://github.com/sudolev/StravaMultiMapper"
                                target="_blank"
                                rel="noopener noreferrer">open-source</a
                            >
                            under the
                            <a
                                href="https://github.com/sudolev/StravaMultiMapper/blob/main/LICENSE"
                                target="_blank"
                                rel="noopener noreferrer">GPL-3.0 license</a
                            >.
                        </p>
                    </Alert.Description>
                </Alert.Root>
            </Card.Footer>
        </Card.Root>
    </div>
</div>
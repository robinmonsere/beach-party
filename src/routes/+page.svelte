<script>
    import './styles.css';
    import '$lib/reset.css';
    import beach_video from "$lib/videos/32.mp4";
    import { injectSpeedInsights } from "@vercel/speed-insights/sveltekit";
    import {onMount} from "svelte";
    injectSpeedInsights();
    const MAPS_API_KEY = import.meta.env.VITE_PUBLIC_MAPS_API_KEY;

    function toggleVideo() {
        const video = document.getElementById('myVideo');
        if (video.paused) {
            video.play();
        } else {
            video.pause();
        }
    }

    function scrollToBottom() {
        window.scrollTo({
            top: document.body.scrollHeight,
            behavior: 'smooth'
        });
    }


</script>

<header>
    <a href="https://www.your-tickets.be/events/BEACHPARTY36theditionSAMEpeopleMOREspace" target="_blank"><h2>
        Tickets</h2></a>
    <span></span>
</header>
<main>
    <section on:click={toggleVideo} id="content">
        <div class="slide-bg" data-parallax>
            <video autoplay muted loop id="myVideo">
                <source src="{beach_video}" type="video/mp4">
            </video>
        </div>
        <div id="slide-content">
            <h1>Beach Party 2024 <br><i>SAME</i> people <br><i>MORE</i> space</h1>
            <i on:click={scrollToBottom} class="fa-solid fa-angle-double-down"></i>
        </div>
    </section>
    <section id="info-container">
        <div id="info">
            <div class="info">
                <h3>Date</h3>
                <p>Sat - 27.04 - 22:00</p>
            </div>
            <div class="info">
                <h3>Socials</h3>
                <div id="links">
                    <a href="https://www.facebook.com/Beachpartyscoutsingelmunster/" target="_blank"><i
                            class="fa-brands fa-facebook-f"></i></a>
                    <a href="https://www.tiktok.com/@scoutsingelmunster" target="_blank"><i
                            class="fa-brands fa-tiktok"></i></a>
                    <a href="https://www.instagram.com/beachpartyscoutsingelmunster/" target="_blank"><i
                            class="fa-brands fa-instagram"></i></a>
                </div>
            </div>
            <div class="info" id="location">
                <h3>Location</h3>
                <p>Festivalweide</p>
                <p>8770 Ingelmunster</p>
                <div id="map">
                    <iframe title="map" width="600" height="300" style="border:0" loading="lazy" allowfullscreen
                            src="https://www.google.com/maps/embed/v1/place?q=place_id:EidUcmFrZWx3ZWcgMSwgODc3MCBJbmdlbG11bnN0ZXIsIEJlbGdpdW0iMBIuChQKEgnHIxt7CDnDRxHrbWeStiQiARABKhQKEgnzAoForznDRxEFN7HfwUSrqQ&key={MAPS_API_KEY}"></iframe>
                </div>
            </div>
        </div>

    </section>
</main>


<style lang="scss">

  main {
    margin: 0;
    padding: 0;
    height: 150vh;
    overscroll-behavior: none;
  }

  header {
    overscroll-behavior: none;
    position: sticky;
    top: 0;
    background-color: transparent;
    display: flex;
    flex-direction: column;
    align-items: end;
    padding: 0.5rem 1rem;
    z-index: 99;
    height: 2.5rem;
    h2 {
      margin: 0;
      width: 100%;
      color: white;
      font-size: 2rem;
      font-weight: bolder;
      padding-bottom: 0.3rem;

      &:hover {
        color: var(--color-theme-2);
      }
    }

    a:hover + span {
      background-color: var(--color-theme-2);
    }

    span {
      width: 100%;
      height: 2px;
      background-color: white;
      border-radius: 1px;
    }
  }

  #content {
    overscroll-behavior: none;
    height: 100vh;
    background-color: transparent;
  }

  @keyframes bounce {
    0%, 20%, 50%, 80%, 100% {
      transform: translateY(0);
    }
    40% {
      transform: translateY(-30px);
    }
    60% {
      transform: translateY(-15px);
    }
  }

  #slide-content {
    display: flex;
    justify-content: space-between;
    align-items: start;
    padding: 1.5rem 1rem;
    flex-direction: column;
    height: 80%;
    .fa-angle-double-down {
      align-self: center;
      font-size: 2rem;
      color: white;
      margin-top: 1rem;
      animation: bounce 2s infinite;
    }
    #pause {
        background: transparent;
        position: absolute;
        border: 0.25rem solid #ffffff;
        border-radius: 50%;
        width: 3rem;
        height: 3rem;
        margin: 0 auto;
        display: flex;
        justify-content: center;
        align-items: center;
        z-index: 2;
        right: 5%;
      color: white;
      font-weight: 900;
      font-size: 1.2rem;
      i.fa-solid {
        background: hotpink;
        color: white;
        font-weight: 900;

      }
      &:hover {
        background-color: white;
        i {
          color: var(--color-theme-2);
        }
      }
    }
    h1 {
      font-weight: 600;
      font-size: 3rem;
      line-height: 1.5;
      color: var(--color-text-1);
      i {
        font-style: italic;

      }
    }
  }

  #info-container {
    display: flex;
    flex-direction: column;
    justify-content: end;
    padding: 0.5rem 1rem;
    background: black;
    //background: black url(../lib/images/BeachBgr.png) no-repeat right 5rem;
    //background-image: linear-gradient(transparent,black, black, black);
    height: 100vh;
    color: white;
    font-weight: 600;
    #info {
      display: flex;
      flex-direction: column;
      height: calc(100vh - 5.5rem);
      justify-content: end;
      gap: 2rem;
      i {
        color: white;
        font-size: 1.5rem;
      }
      h3 {
        font-size: 1.5rem;
        margin: 0.2rem 0;
        padding-bottom: 0.5rem;
        text-decoration: underline var(--color-text-1);
      }

      #location {
        flex-grow: 0;
      }
      #links {
        display: flex;
        gap: 1rem;
      }
      #map {
        margin-top: 1rem;
        height: 25rem;
        width: 50%;
        iframe {
          border-radius: 0.5rem;
          height: 100%;
          width: 100%;
        }
      }
    }
  }

  .slide-bg {
    position: fixed;
    height: 100vh;
    width: 100vw;
    object-fit: cover;
    overflow: hidden;
    top: 0;
    left: 0;
    z-index: -1;
  }

  #myVideo {
    width: 100%;
    height: 100%;
    object-fit: cover;
  }

  @media screen and (max-width: 950px) {
    #slide-content {
      h1 {
        font-size: 6vw;
        line-height: 1.5;
      }
    }

    header {
      a:hover  {
        h2{
          color: var(--color-text-1);
        }

        + span {
          background-color: var(--color-text-1);
        }
      }
    }
    #info-container {
      background-image: none;
      #info {
        //justify-content: space-between;
        gap: 1rem;
        #map {
          width: 100%;
          height: 40vh;
          iframe {
            height: 100%;
            width: 100%;
          }
        }
      }
    }
  }

  @media screen and (max-height: 500px) {
    #info-container {
      #info {
        #map {
          height: 20vh;
        }
      }
    }
  }

</style>
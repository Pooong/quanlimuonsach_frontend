<template>
    <div class="containPage">
      
      <div class="contentPage">
        <div class="wrap-banner">
          <section class="banner">
          <img class="img_item" style="width: 100%;" src="../../../assets/bg-home.jpg" alt="" />
            <div class="text-center text-lg-start">
              <div class="container">
                <div class="row gx-lg-5 align-items-center">
                  <div class="col-lg-6 my-5 mb-lg-0">
                    <div class="titlePage">
                    <h2>
                      Welcome to
                      <span class="titleWeb">F<span class="text-light">BOOKS</span></span>
                    </h2>
                </div>
                    <h1 class="fw-bold ls-tight titleIntro">
                      There is no friend as loyal as a
                      <span class="titleWeb"
                        >Book.<span class="text-dark"></span
                      ></span>
                      <br />
                      <span class="text-primary">(Ernest Hemingway)</span>
                    </h1>
                    <p class="text-light">
                      Books are not only pages filled with knowledge, but also doors
                      opening to new worlds, endless sources of inspiration, and
                      loyal companions in the loneliest moments of life. Within each
                      page, we discover not only the culture, history, and
                      philosophy of humanity but also encounter wonders, adventures,
                      and valuable lessons for ourselves.
                    </p>
                    
                    <router-link to="/about" class="text-decoration-none">
                      <button class="btnReadMore">Order now</button>
                    </router-link>
                  </div>
                  <!-- <div class="col-lg-6 mb-5 mb-lg-0">
                    <div class="card">
                      <div class="imageCup">
                      
                      </div>
                      
                    </div>
                    <img style="width: 100%;" src="../../../assets/bg-home.jpg" alt="" />
                  </div> -->
                </div>
              </div>
            </div>
          </section>
        </div>
        <div class="wrap-banner">
          <section class="banner">
          <img class="img_item" style="width: 100%;" src="../../../assets/slide6.jpg" alt="" />
            <div class="text-center text-lg-start">
              <div class="container">
                <div class="row gx-lg-5 align-items-center">
                  <div class="col-lg-6 mb-5 my-5 mb-lg-0">
                    <div class="titlePage">
                    <h2>
                      Welcome to
                      <span class="titleWeb">F<span class="text-light">BOOKS</span></span>
                    </h2>
                </div>
                    <h1 class=" fw-bold ls-tight titleIntro">
                      There is no friend as loyal as a
                      <span class="titleWeb"
                        >Book.<span class="text-dark"></span
                      ></span>
                      <br />
                      <span class="text-primary">(Ernest Hemingway)</span>
                    </h1>
                    <p class="text-light">
                      Books are not only pages filled with knowledge, but also doors
                      opening to new worlds, endless sources of inspiration, and
                      loyal companions in the loneliest moments of life. Within each
                      page, we discover not only the culture, history, and
                      philosophy of humanity but also encounter wonders, adventures,
                      and valuable lessons for ourselves.
                    </p>
                    
                    <router-link to="/about" class="text-decoration-none">
                      <button class="btnReadMore">Order now</button>
                    </router-link>
                  </div>
                  <!-- <div class="col-lg-6 mb-5 mb-lg-0">
                    <div class="card">
                      <div class="imageCup">
                      
                      </div>
                      
                    </div>
                    <img style="width: 100%;" src="../../../assets/bg-home.jpg" alt="" />
                  </div> -->
                </div>
              </div>
            </div>
          </section>
        </div>
        <div class="wrap-banner">
          <section class="banner">
          <img class="img_item" style="width: 100%;" src="../../../assets/slide5.jpg" alt="" />
            <div class="text-center text-lg-start">
              <div class="container">
                <div class="row gx-lg-5 align-items-center">
                  <div class="col-lg-6 mb-5 my-5 mb-lg-0">
                    <div class="titlePage">
                    <h2>
                      Welcome to
                      <span class="titleWeb">F<span class="text-light">BOOKS</span></span>
                    </h2>
                </div>
                    <h1 class="fw-bold ls-tight titleIntro">
                      There is no friend as loyal as a
                      <span class="titleWeb"
                        >Book.<span class="text-dark"></span
                      ></span>
                      <br />
                      <span class="text-primary">(Ernest Hemingway)</span>
                    </h1>
                    <p class="text-light">
                      Books are not only pages filled with knowledge, but also doors
                      opening to new worlds, endless sources of inspiration, and
                      loyal companions in the loneliest moments of life. Within each
                      page, we discover not only the culture, history, and
                      philosophy of humanity but also encounter wonders, adventures,
                      and valuable lessons for ourselves.
                    </p>
                    
                    <router-link to="/about" class="text-decoration-none">
                      <button class="btnReadMore">Order now</button>
                    </router-link>
                  </div>
                  <!-- <div class="col-lg-6 mb-5 mb-lg-0">
                    <div class="card">
                      <div class="imageCup">
                      
                      </div>
                      
                    </div>
                    <img style="width: 100%;" src="../../../assets/bg-home.jpg" alt="" />
                  </div> -->
                </div>
              </div>
            </div>
          </section>
        </div>  
      </div>
    </div>
  </template>
  
  <script>
  document.addEventListener('DOMContentLoaded', function() {
    function rotateBanners() {
      const bannersContainer = document.querySelector('.contentPage');
      const banners = bannersContainer.querySelectorAll('.wrap-banner');
      const firstBanner = banners[0];
      const bannerClone = firstBanner.cloneNode(true);

      bannersContainer.appendChild(bannerClone); 
      bannersContainer.removeChild(firstBanner); 

      setTimeout(() => {
        bannersContainer.insertBefore(bannerClone, banners[0]);
        bannerClone.classList.remove('animated');
        void bannerClone.offsetWidth; // Trigger reflow
        bannerClone.classList.add('animated');
      }, 10);
    }

    setInterval(rotateBanners, 3000);
  });
</script>

  
  <style lang="scss" scoped>
  @import "./Home.scss";
  </style>
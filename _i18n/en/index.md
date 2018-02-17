<html>
  {% include head.html %}
   <body>
    <div id="page">
      <nav class="mobile-nav mob-nav">
                    <div class="row logo-wrap start-xs middle-xs">
                        <div class="col-xs-12">
                            <a href="index.html"><img src="/img/monerujo_logo.png" alt="Monerujo Logo" class="logo"></a>
                        </div> 
                    </div>
                    <input class="burger-check" id="mobile-burger" type="checkbox">
                    <label for="mobile-burger" class="hamburger hamburger--collapse">
                        <span class="hamburger-box">
                            <span class="hamburger-inner"></span>
                        </span>
                    </label>
                    <div class="slide-in-nav">
                        <div class="row center-xs">
                            <div class="col-xs-12">
                                <ul>
                                    {% for item in site.data.lang[site.lang].navigation %}
                                    <li class="nav-item">
                                        <a href="{{item.url}}">{{item.title}}</a>
                                    </li>
                                     {%endfor%}
                                </ul>
                            </div>
                        </div>         
                    </div>
               </nav>
       <div class="container-fluid" id="hero">      
        <header class="container">               
               <nav class="desktop-nav container">
                    <div class="row middle-xs nav-items">
                            <div class="col-sm-5">
                                <a href="index.html" class="logo-wrap"><img src="/img/monerujo_logo.png" alt="Monerujo Logo" class="logo"></a>
                            </div>
                            <div class="col-sm-7">
                                <div class="row end-xs">
                                    {% for item in site.data.lang[site.lang].navigation %}
                                    <div class="col nav-item">
                                        <a href="{{item.url}}">{{item.title}}</a>
                                    </div>
                                     {%endfor%}
                                </div>
                            </div>       
                    </div>
               </nav>
           </header>
           <section class="container" id="hero_content">
                    <div class="row middle-xs">
                       <div class="col-sm-6 col-xs-6 hero-img">
                          <div class="row middle-xs center-xs hero-row">
                              <div class="col-xs-12">
                                  <img src="/img/gunther-hello-800x.gif" alt="Gunther Greeting" class="gunther-greeting">
                              </div>
                          </div>
                       </div>
                       <div class="col-sm-6 col-xs-6 info">
                                    <h1><span>Monerujo</span> <br>Android Wallet for Monero</h1>
                                       <a href="https://play.google.com/store/apps/details?id=com.m2049r.xmrwallet" class="btn btn-large">Download</a>
                                       <a href="https://github.com/m2049r/xmrwallet/tree/v1.2.1/doc" class="btn btn-secondary btn-large">Docs</a>
                       </div>
                    </div>
           </section>
        </div>  
        <section class="container-fluid features" id="about">
                <div class="site-section container">
                   <div class="row middle-xs">
                     <div class="col-sm-6 col-xs-7 col">
                          <h2>Multiple Wallets</h2>
                          <p>With Monerujo, you can seamlessly move back and forth between several wallets. Making a new one is as simple as a few taps.</p>
                      </div>
                      <div class="col-sm-6 col-xs-5 col">
                          <img src="/img/gunther-wallets-800x.gif" alt="" class="feature_img">
                      </div>
                    </div>
                </div>
        </section>
        <section class="container-fluid features" id="grey">
                <div class="site-section container">
                    <div class="row middle-xs">
                      <div class="col-sm-6 col-xs-5 col">
                          <img src="/img/gunther-qrcode-800x.gif" alt="" class="feature_img"/>
                      </div>
                      <div class="col-sm-6 col-xs-7 col">
                          <h2>QR Code Scanning</h2>
                          <p>Typing in Monero addresses manually is a pain. That's why Monerujo comes with a built in QR scanner. Just scan and then send. It's that easy.</p>
                      </div>
                    </div>
                </div>
        </section>
        <section class="container-fluid features" id="opensource">
                <div class="site-section container">
                    <div class="row middle-xs">
                      <div class="col-sm-6 col-xs-7 col">
                          <h2>Open Source</h2>
                          <p>Monerujo is completely open source. This means that anyone and everyone can look at our code to ensure security. You can have peace of mind and know that your money is safe, something that would not be present if we were proprietary software.</p>
                      </div>
                      <div class="col-sm-6 col-xs-5 col">
                          <img src="/img/gunther-omm-800x.gif" alt="" class="feature_img"/>
                      </div>
                    </div>
                   </div>
        </section>
        <section class="container-fluid features" id="grey">
                <div class="site-section container">
                    <div class="row middle-xs">
                      <div class="col-sm-6 col-xs-7 col">
                          <h2>Pay BTC Addresses</h2>
                          <p>With the power of the XMR.to service, Monerujo can now pay any BTC address. Just scan the QR code or paste the BTC address into the send field, and the magic happens seamlessly in the background.</p>
                      </div>
                      <div class="col-sm-6 col-xs-5 col">
                          <img src="/img/mortalgunther_animated_800x.gif" alt="" class="feature_img"/>
                      </div>
                    </div>
                   </div>
        </section>
        <section class="container-fluid" id="download"> 
                <div class="site-section container">
                   <div class="row">
                       <div class="col-xs-12">
                           <h2>Download Monerujo</h2>
                           <h4>Monerujo is available for download on Google Play</h4>
                           <p><a href="https://play.google.com/store/apps/details?id=com.m2049r.xmrwallet"><img src="/img/google-play-badge.png" alt="Google Play Badge" class="gp-badge"></a></p>
                       </div>
                   </div>
                </div>
           </section>    
            {% include footer.html %}
     </div>
  </body>
</html>

---
layout: pricing
category: pricing
title: pricing
---

<section class="bg-blue">
<div class="container">
    <div class="row">
        <div class="col-md-12">
            <p class="main-heading">Pricing</p>
            <p class="header-text">Transform unlimited notes into the tools you use everyday.</p>
            <p class="header-text">Go from meeting outcomes to action items in seconds.</p>
        </div>
    </div>
    <div class="row">
        <div class="col-6 col-md-6" id="btn1">
            <button type="button" class="monthBtn" id="monthbtn" onclick="monthlyPrice()">Monthly</button>
        </div>
        <div class="col-6 col-md-6" id="btn2">
            <button type="button" class="annualBtn" id="annualbtn" onclick="annualPrice()">Annually
        </button>
        </div>
        <div class="col-md-12">
            <p class="underBtntext">Save 40% with annual billing</p>
        </div>
    </div>
    <div class="row" id="card-box">
        <div class="col-10 col-sm-8 col-md-5 col-lg-3 cards" id="card1">
            <div class="row" >
                <div class="col-md-12">
                    <p class="card-heading">Lite</p>
                </div>
            </div>
            <div class="row">
                <div class="col-xs-8 col-md-12 price-text">
                    <h1 id="price1">$6</h1>
                    <h5>/month</h5>
                    <p>billed annually</p>
                </div>
            </div>
            <div class="row price-text-second">
                <div class="col-xs-8 col-md-12 ">
                    <h3>Includes</h3>
                    <h4>Unlimited notes</h4>
                    <hr>
                    <h5>Sync to Trello</h5>
                </div>
                <div class="col-12 col-md-12 col-lg-12" >
                    <button type="button" class="buyBtn" id="liteBuyBtn">Buy</button>
                    <button type="button" class="buyBtn" id="liteBuyBtn2" style="display:none">Buy</button>
                </div>
            </div>
        </div>
        <div class="col-md-2 col-lg-1"></div>
        <div class="col-10 col-sm-8 col-md-5 col-lg-4 cards">
            <div class="row" >
                <div class="col-md-12">
                    <p class="card-heading">Pro</p>
                </div>
            </div>
            <div class="row">
                <div class="col-md-12 price-text2">
                    <h2>Most Popular</h2>
                    <h1 id="price2">$14</h1>
                    <h5>/month</h5>
                    <p>billed annually</p>
                </div>
            </div>
            <div class="row price-text-second" id="pricecard2">
                <div class="col-md-12 ">
                    <h3>Includes</h3>
                    <h4>Unlimited notes</h4>
                    <hr>
                    <h5>Sync to Trello</h5>
                    <hr>
                    <h5>Sync to Jira Cloud</h5>
                    <hr>
                    <h5>Sync to Jira Server</h5>
                </div>
                <div class="col-12 col-md-12 col-lg-12" >
                    <button type="button" class="buyBtn-card2" id="proBuyBtn">Buy</button>
                    <button type="button" class="buyBtn-card2" id="proBuyBtn2"  style="display:none">Buy</button>
                </div>
            </div>
        </div>
        <div class=" col-md-1"></div>
        <div class="col-10 col-sm-8 col-md-5 col-lg-3 cards" id="card3">
            <div class="row" >
                <div class="col-md-12">
                    <p class="card-heading">Team</p>
                </div>
            </div>
            <div class="row">
                <div class="col-md-12 price-text3">
                    <h1>Custom</h1>
                    <p>for more than ten accounts</p>
                </div>
            </div>
            <div class="row price-text-second-card3">
                <div class="col-md-12 ">
                    <h3>Get in touch to discuss how we can help connect your team.</h3>
                </div>
                <div class="col-md-12">
                    <button type="button" class="ContactBtn" onclick="window.location.href='mailto:magic@wallsync.net'">Contact Us</button>
                </div>
            </div>
        </div>
    </div>
</div>
</section>
<img src="/images/Rectangle2.png" class="img-fluid banner-after-bg">
<section class="base-text container">
    <div class="row">
        <div class="col-md-12">
            <h1>Not sure which plan will suit you best?</h1>
            <h2>Start a free 14 day trial with access to all features.</h2>
        </div>
        <div class="col-md-12">
            <button type="button" class="TrialBtn" onclick="window.location.href='/index.html'" >Start free trial</button>
        </div>
    </div>
</section>
<div id="error-message"></div>
<script src="https://js.stripe.com/v3"></script>
 <script type="text/javascript">
    window.onload = function() {
       document.getElementById("annualbtn").classList.remove("annualBtn-inactive");
       document.getElementById("monthbtn").classList.add("monthBtn-inactive"); 
       annualPrice()
    }
    //test key
    //var stripe = Stripe('pk_test_eBAjT4DvCokUwfzvtuKTzWQw00M2bwrQPC');
    var stripe = Stripe('pk_live_fbBE1G1aI6nXlM8qMynRRlco006FxAxZ5O');
    var pricelite=document.getElementById("price1");
    var pricepro=document.getElementById("price2");
    var probuy=document.getElementById("proBuyBtn");
    var litebuy=document.getElementById("liteBuyBtn");
    var litebuy2=document.getElementById("liteBuyBtn2");
    var probuy2=document.getElementById("proBuyBtn2");
    var probuyannual="plan_FG0r5zPJohwZKY";
    var litebuyannual = "plan_FG0tJWuvSl7lXp";
    var probuymonthly="plan_FG0r4oSpDrSTlc";
    var litebuymonthly="plan_FG0sSWeImScIco";
    function monthlyPrice(){
       document.getElementById("annualbtn").classList.add("annualBtn-inactive");
       document.getElementById("monthbtn").classList.remove("monthBtn-inactive");
       probuy2.style.display = "block";
       probuy.style.display = "none";
       litebuy2.style.display = "block";
       litebuy.style.display = "none";
       pricelite.innerHTML = "$10";
       pricepro.innerHTML= "$20";
       probuy2.addEventListener('click', function () {
           CallStripe(probuymonthly);
           });
       litebuy2.addEventListener('click', function () {
            CallStripe(litebuymonthly);
        });
    }
    function annualPrice(){
       document.getElementById("annualbtn").classList.remove("annualBtn-inactive");
       document.getElementById("monthbtn").classList.add("monthBtn-inactive");  
       probuy2.style.display = "none";
       probuy.style.display = "block";
       litebuy2.style.display = "none";
       litebuy.style.display = "block";
       pricelite.innerHTML = "$6";
       pricepro.innerHTML= "$14"; 
       probuy.addEventListener('click', function () {
           CallStripe(probuyannual);
        });
       litebuy.addEventListener('click', function(){
            CallStripe(litebuyannual);
        });
    }
    function CallStripe(var1){
        stripe.redirectToCheckout({
        items: [{plan: var1, quantity: 1}],
        successUrl: 'https://www.wallsync.net/capture/pricing/success',
        cancelUrl: 'https://www.wallsync.net/capture/pricing/cancelled',
        })
        .then(function (result) {
        if (result.error) {
            var displayError = document.getElementById('error-message');
            displayError.textContent = result.error.message;
        }
        });
    }
 </script>







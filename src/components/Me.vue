<template>
  <section class="container">
    <div>
      <h1 class="title">
        Ender Bonnet
      </h1>
      <h2 class="subtitle">
        <a href="#" class="typewrite" data-period="2000" data-type='[ "Hola, soy @enBonnet", "I Love JavaScript", "Construido con Vue" ]'>
          <span class="wrap"></span>
        </a>
      </h2>
      <div class="rrss">
        <div class="twitter">
          <a href="https://twitter.com/enBonnet">
            <i class="fab fa-twitter-square"></i>
          </a>
        </div>
        <div class="instagram">
          <a href="https://www.instagram.com/enbonnet/">
            <i class="fab fa-instagram"></i>
          </a>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
import Timeline from "vue-tweet-embed/timeline";

var TxtType = function(el, toRotate, period) {
  this.toRotate = toRotate;
  this.el = el;
  this.loopNum = 0;
  this.period = parseInt(period, 10) || 2000;
  this.txt = "";
  this.tick();
  this.isDeleting = false;
};

TxtType.prototype.tick = function() {
  var i = this.loopNum % this.toRotate.length;
  var fullTxt = this.toRotate[i];

  if (this.isDeleting) {
    this.txt = fullTxt.substring(0, this.txt.length - 1);
  } else {
    this.txt = fullTxt.substring(0, this.txt.length + 1);
  }

  this.el.innerHTML = '<span class="wrap">' + this.txt + "</span>";

  var that = this;
  var delta = 200 - Math.random() * 100;

  if (this.isDeleting) {
    delta /= 2;
  }

  if (!this.isDeleting && this.txt === fullTxt) {
    delta = this.period;
    this.isDeleting = true;
  } else if (this.isDeleting && this.txt === "") {
    this.isDeleting = false;
    this.loopNum++;
    delta = 500;
  }

  setTimeout(function() {
    that.tick();
  }, delta);
};

window.onload = function() {
  var elements = document.getElementsByClassName("typewrite");
  for (var i = 0; i < elements.length; i++) {
    var toRotate = elements[i].getAttribute("data-type");
    var period = elements[i].getAttribute("data-period");
    if (toRotate) {
      new TxtType(elements[i], JSON.parse(toRotate), period);
    }
  }
  // INJECT CSS
  var css = document.createElement("style");
  css.type = "text/css";
  css.innerHTML = ".typewrite > .wrap { border-right: 0.08em solid #000}";
  document.body.appendChild(css);
};

export default {
  name: "Me"
};
</script>

<style scoped>
.container {
  color: #666666;
  font-family: "Open Sans", sans-serif;
  display: flex;
  justify-content: center;
}

.container .title {
  text-align: center;
  font-weight: 400;
  letter-spacing: 0.2rem;
}

.container .subtitle a {
  color: #666666;
  text-decoration: none;
  text-align: center;
  font-weight: 300;
}

.container .rrss {
  display: flex;
  justify-content: center;
  font-size: 3em;
}

.container .rrss .twitter a {
  color: #666666;
  transition: color 1s;
  margin-right: 10px;
}

.container .rrss .twitter a:hover {
  color: #00aced;
}

.container .rrss .instagram a {
  color: #666666;
  transition: color 1s;
}

.container .rrss .instagram a:hover {
  color: #e1306c;
}
</style>

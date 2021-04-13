---
title: You are logged in!
type: managed
subtitle: Let us know what you think about the login experience. No more passwords. No more friction. No more security holes.
featured_image: /assets/img/flows/welcome.jpg
---
<script src="https://unpkg.com/@lottiefiles/lottie-player@latest/dist/lottie-player.js"></script>
<script src="/jwt-decode.js"></script>

<!-- Definition -->
<div class="section">
  <div class="container">
    <div class="row">
      <div class="col-lg-6 mx-auto mx-auto justify-content-center d-flex flex-column">
        <h6 class="text-uppercase">Login details</h6>
        <h3 class="display-3">JWT token your app will receive</h3>
		<p>Your application will receive a JWT token to identify the user. The example of the token is below:</p>
     	 <pre id="jwt"></pre>
	  </div>
      <div class="col-lg-6 mx-auto">
          <img src="/assets/img/flows/signed.png">
      </div>
    </div>
  </div>
</div>

<script>
	function urlParam(name){
	  var results = new RegExp('[?&]' + name + '=([^&#]*)').exec(window.location.href);
	  if (results == null){
	     return null;
	  }
	  else {
	     return decodeURI(results[1]) || 0;
	  }
	}
	
	const idToken = urlParam('idToken');
	console.log("IdToken:"+ idToken);
	 // just decode 'token' into {header: Object, payload: Object, signature: String}
	 let claims = jwt_decode(idToken);
	 document.getElementById("jwt").innerHTML = JSON.stringify(claims, undefined, 2);
</script>

<!-- Contact us for demo -->
<div id="main" class="container mt-5">
<div class="section bg-primary">
  <div class="container">
    <div class="row">
      <div class="col-md-6 mx-auto text-center">
          <h3 class=" display-3 text-neutral">Curious to learn more?</h3>
          <p class="text-neutral">Let us know, and we will be happy to help</p>
      </div>
    </div>
    <div class="row">
      <div class="col-md-6 mx-auto text-center">
        <a href="https://docs.idemeum.com" target="_blank">
          <button type="submit" class="btn btn-success">Read docs</button>
        </a>
        <a href="https://join.slack.com/t/idemeum-community/shared_invite/zt-npfwnoud-hOjc6rbmZmdTAY3xE3i5FA" target="_blank">
          <button type="submit" class="btn btn-outline-white">Contact on Slack</button>
        </a>
      </div>
    </div>
  </div>
</div>
</div>

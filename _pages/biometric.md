---
title: Biometric Passwordless Login
subtitle: <p id="add" class="lead">Frictionless login that combines the power of JWT tokens and biometrics with Webauthn. You can use external or built-in authenticators such as fingerprint scanner or a Yubikey.</p><a id="try"><button type="button" class="btn btn-icon btn-primary mt-3 fixed-width1 ml-1 mr-1" onclick="login()"><span class="btn-inner--icon"><i class="fas fa-fingerprint"></i></span><span class="btn-inner--text">Try biometric login</span></button></a><a id="replace"><button type="button" class="btn btn-icon btn-3 btn-warning mt-3 fixed-width1 disabled">Not supported</button></a><a href="https://docs.idemeum.com/overview/biometric/" target="_blank"><button type="button" class="btn btn-outline-white mt-3 fixed-width1 ml-1 mr-1">Learn more</button></a>
featured_image: /assets/img/flows/biometric.jpg
type: full-view
---
<script src="https://kit.fontawesome.com/db82ff0024.js" crossorigin="anonymous"></script>

<script type="text/javascript" src="https://code.jquery.com/jquery-3.4.1.min.js"></script>
<script src="https://asset.idemeum.com/webapp/SDK/idemeum.js"></script>

<script src="/ua-parser.js"></script>

<script>
	var parser = new UAParser();
	var browser = parser.getBrowser().name;
	var os = parser.getOS().name;
	var result = browser + '_' + os;
	
	console.log(browser);
	console.log(os);
	console.log(result);
	
	var browser_list = ['Chrome_Windows', 'Chrome_Android', 'Chrome_Mac OS', 'Chrome_iOS', 'Safari_Mac OS', 'Mobile Safari_iOS', 'Firefox_Windows', 'Edge_Windows', 'Edge_Mac OS']
	if (browser_list.includes(result)) {
		
		var firstbtn = document.getElementById("try");
		var secondbtn = document.getElementById("replace");
		firstbtn.parentNode.replaceChild(firstbtn, secondbtn);
		
	    
		
	    var oidc = {};
	
	    var idemeum = new IdemeumManager(
	      // 👈 Replace clientId with the the one you get from idemeum developer portal
	      (clientId = "5166e6ac-9442-11eb-a8b3-0242ac130003")
	    );
	
	    function login() {
         idemeum
            .login()
            .then(function (signinResponse) {
              // Your application will receive ID and Access tokens from idemeum
              // renderUserClaims() (defined below) validates the oidc token and fetches the user approved claims
  	        oidc = signinResponse.oidc;
  		    window.open("/loggedin.html?idToken="+ oidc.idToken, "_self")
            })
            .catch(function (errorResponse) {
              // If there is an error you can process it here
            });
	    }
		
		
		
		
		
	} else {
		
		var element = document.getElementById("add");
		
		element.insertAdjacentHTML('afterend', '<p class="mt-3 text-warning"><strong>Your browser does not support WebAuthn. Please, check the <a href="https://docs.idemeum.com/knowledgebase/browser-support/" target ="_blank" class="link-red">browser support matrix</a>.</strong></p>');
		

		var firstbtn = document.getElementById("try");
		var secondbtn = document.getElementById("replace");
		firstbtn.parentNode.replaceChild(secondbtn, firstbtn);	
		
	}
	
</script>
	
	
	
	
	
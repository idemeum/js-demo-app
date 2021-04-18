---
title: Biometric Passwordless Login
subtitle: <p id="add" class="lead">Frictionless login that combines the power of JWT tokens and biometrics with Webauthn. You can use external or built-in authenticators such as fingerprint scanner or a Yubikey.</p><a id="try"><button type="button" class="btn btn-icon btn-primary mt-3 fixed-width1 ml-1 mr-1" onclick="idemeum.signin()"><span class="btn-inner--icon"><i class="fas fa-fingerprint"></i></span><span class="btn-inner--text">Try biometric login</span></button></a><a id="replace"><button type="button" class="btn btn-icon btn-3 btn-warning mt-3 fixed-width1 disabled">Not supported</button></a><a href="https://docs.idemeum.com/overview/biometric/" target="_blank"><button type="button" class="btn btn-outline-white mt-3 fixed-width1 ml-1 mr-1">Learn more</button></a>
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
	console.log(browser);
	console.log(typeof browser);
	
	var browser_list = ['Chrome', 'Safari']
	
	if (browser_list.includes(browser)) {
		
		var firstbtn = document.getElementById("try");
		var secondbtn = document.getElementById("replace");
		firstbtn.parentNode.replaceChild(firstbtn, secondbtn);
		
	    var oidc = {};
	    // Initialize Idemeum sdk with with client ID
	    var idemeum = new IdemeumManager(
	        {
	            clientId: '5166e6ac-9442-11eb-a8b3-0242ac130003',
	            onSuccess: function (signinResponse) {
	                // Fetch OIDC Token from the signin response
	                oidc = signinResponse.oidc;
					window.open("/loggedin.html?idToken="+ oidc.idToken, "_self")
				
	            },
	            onError: function (errorResponse) {
                
	            }
	        });

	    function validateToken() {
	        // use OIDC token received in sign in response to get user approved claims
	        idemeum.getUserClaims(oidc).then(function (userClaimsResponse) {
	            //fetch user approved claims from JSON response
	        }).catch(function (errorResponse) {

	        });
	    }		
		
	} else {
		
		var element = document.getElementById("add");
		
		element.insertAdjacentHTML('afterend', '<p class="mt-3 text-warning"><strong>Your browser does not support WebAuthn. Please, check the <a href="https://fidoalliance.org/fido2/fido2-web-authentication-webauthn/" target ="_blank" class="link-red">browser support matrix</a>.</strong></p>');
		

		var firstbtn = document.getElementById("try");
		var secondbtn = document.getElementById("replace");
		firstbtn.parentNode.replaceChild(secondbtn, firstbtn);	
		
	}
	
</script>
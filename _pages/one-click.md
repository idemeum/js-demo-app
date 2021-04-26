---
title: One-Click Passwordless Login
subtitle: <p class="lead">Simplest and most frictionless type of idemeum flow to log in your users with just a click of a button.</p><a><button type="button" class="btn btn-icon btn-primary mt-3 fixed-width1 ml-1 mr-1" onclick="login()"><span class="btn-inner--icon"><i class="fas fa-mouse"></i></i></span><span class="btn-inner--text">Try one-click login</span></button></a><a href="https://docs.idemeum.com/overview/oneclick/" target="_blank"><button type="button" class="btn btn-outline-white mt-3 fixed-width1 ml-1 mr-1">Learn more</button></a>
featured_image: /assets/img/flows/one-click.jpg
type: full-view
---
<script src="https://kit.fontawesome.com/db82ff0024.js" crossorigin="anonymous"></script>

<script type="text/javascript" src="https://code.jquery.com/jquery-3.4.1.min.js"></script>
<script src="https://asset.idemeum.com/webapp/SDK/idemeum.js"></script>

<script type="text/javascript">
    var oidc = {};
	
    var idemeum = new IdemeumManager(
      // 👈 Replace clientId with the the one you get from idemeum developer portal
      (clientId = "00000000-0000-0000-0000-000000000000")
    );
	
    function login() {
      idemeum.login({
        onSuccess: function (signinResponse) {
          // Your application will receive ID and Access tokens from idemeum
          // getUserClaims validates the oidc token and fetches the user approved claims
          // Fetch OIDC Token from the signin response
          oidc = signinResponse.oidc;
	      window.open("/loggedin.html?idToken="+ oidc.idToken, "_self")
          
        },
        onError: function (errorResponse) {
          // If there is an error you can process it here
        }
      });
    }
</script>	
				

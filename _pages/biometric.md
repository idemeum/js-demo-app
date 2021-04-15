---
title: Biometric Passwordless Login
subtitle: Frictionless login that combines the power of JWT tokens and biometrics with Webauthn. <br><button type="button" class="btn btn-icon btn-3 btn-primary mt-3 fixed-width1" onclick="idemeum.signin()"><span class="btn-inner--icon"><i class="fas fa-fingerprint"></i></span><span class="btn-inner--text">Try biometric login</span></button><a href="https://docs.idemeum.com/overview/biometric/" target="_blank"><button type="button" class="btn btn-outline-white mt-3">Docs</button></a>
featured_image: /assets/img/flows/biometric.jpg
type: full-view
---
<script src="https://kit.fontawesome.com/db82ff0024.js" crossorigin="anonymous"></script>

<script type="text/javascript" src="https://code.jquery.com/jquery-3.4.1.min.js"></script>
<script src="https://asset.idemeum.com/webapp/SDK/idemeum.js"></script>

<script type="text/javascript">
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
</script>
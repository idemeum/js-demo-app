---
title: Mobile App Passwordless Login
subtitle: The most secure, multi-factor login flow with idemeum mobile app.<br><button type="button" class="btn btn-icon btn-3 btn-primary mt-3 fixed-width1" onclick="idemeum.LoginPage()"><span class="btn-inner--icon"><i class="fas fa-mobile"></i></span><span class="btn-inner--text">Try mobile app login</span></button><a href="https://docs.idemeum.com/overview/loginapp/" target="_blank"><button type="button" class="btn btn-outline-white mt-3">Docs</button></a>
featured_image: /assets/img/flows/mobile-app.jpg
type: full-view
---
<script src="https://kit.fontawesome.com/db82ff0024.js" crossorigin="anonymous"></script>
<script type="text/javascript" src="https://code.jquery.com/jquery-3.4.1.min.js"></script>
<script src="https://asset.idemeum.com/webapp/SDK/idemuam-login3.js"></script>

<script type="text/javascript">
	        var idemeum = new IdemeumLogin(
	            {
	                clientId: 'c1d84ad4-9442-11eb-a8b3-0242ac130003',
	                callback: function(data) {
	                    console.log(data);
	                    debugger;
	                    var d=JSON.parse(data);
	                    if(d.status) {
                      
							alert(d.oidc.idToken);
	                        window.open("/loggedin.html?idToken="+ d.oidc.idToken, "_self")
	                    } else {
	                        alert("message:"+d.message);
	                    }
                    
	                }
	            });
        
</script>
        
    
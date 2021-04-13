---
title: One-Click Passwordless Login
subtitle: Simplest and most frictionless type of idemeum flow to log in your users with just a click of a button. <br><button type="button" class="btn btn-icon btn-3 btn-primary mt-3" onclick="idemeum.LoginPage()"><span class="btn-inner--icon"><i class="fas fa-mouse"></i></i></span><span class="btn-inner--text">Try one-click login</span><a href="https://docs.idemeum.com/overview/oneclick/" target="_blank"><button type="button" class="btn btn-outline-white mt-3">Docs</button></a>
featured_image: /assets/img/flows/one-click.jpg
type: full-view
---
<script src="https://kit.fontawesome.com/db82ff0024.js" crossorigin="anonymous"></script>

<script type="text/javascript" src="https://code.jquery.com/jquery-3.4.1.min.js"></script>
<script src="https://asset.idemeum.com/webapp/SDK/idemuam-login3.js"></script>

<script type="text/javascript">
	        var idemeum = new IdemeumLogin(
	            {
	                clientId: '00000000-0000-0000-0000-000000000000',
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
				

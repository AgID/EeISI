// Function to hide the contents
function hide(c) {

    var hideEl = document.getElementById("hide"+c);
    var showEl = document.getElementById("show"+c);
    var expandEl = document.getElementById("expand"+c);

	if(!hideEl || !showEl) {
	    return;
	}

	hideEl.style.display = "none";
	showEl.style.display = "block";

	var el = document.getElementsByClassName(c+"Block");
	for (var i = 0; i < el.length; i++){
        el[i].style.display = "none";
    }

	if (c != "" && c != "http" && expandEl) {
		expandEl.style.display = "block";
	}
}

// Function to show the content
function show(c) {

    var hideEl = document.getElementById("hide"+c);
    var showEl = document.getElementById("show"+c);
    var expandEl = document.getElementById("expand"+c);

    if(!hideEl || !showEl) {
        return;
    }

	hideEl.style.display = "block";
	showEl.style.display = "none";

	var el = document.getElementsByClassName(c+"Block");
	for (var i = 0; i < el.length; i++){
        el[i].style.display = "";
    }

	if (c != "" && c != "http" && expandEl) {
		expandEl.style.display = "none";
	}
}

// Binds show/hide buttons
var chainCount = document.getElementById("chainCount").value;
for (var i = 1; i <= chainCount; i++) {

    // Binds Certification Paths buttons
    var hideCert = document.getElementById('hidecert'+i);
    var showCert = document.getElementById('showcert'+i);
    var expandCert = document.getElementById('expandcert'+i);
    if(hideCert && showCert && expandCert ) {
            hideCert.onclick = function() {
                hide(this.getAttribute("cert"));
            }

            showCert.onclick = function() {
                show(this.getAttribute("cert"));
            }

            expandCert.onclick = function() {
                show(this.getAttribute("cert"));
            }
    }

    // Bind buttons to Server Certifcate section
    var hideChain = document.getElementById('hidechain'+i);
    var showChain = document.getElementById('showchain'+i);
    var expandChain = document.getElementById('expandchain'+i);

    if (document.getElementById('hidechain'+i) && document.getElementById('showchain'+i) && document.getElementById('expandchain'+i)) {
        document.getElementById('hidechain'+i).onclick = function() {
            hide(this.getAttribute("cert"));
        }

        document.getElementById('showchain'+i).onclick = function() {
            show(this.getAttribute("cert"));
        }

        document.getElementById('expandchain'+i).onclick = function() {
            show(this.getAttribute("cert"));
        }
    }

    // Hide on initial load
    hide('cert'+i);
    hide('chain'+i);
}

//Bind buttons to cipher suites block section
var protocolCount = document.getElementById("protocolCount");
var identicalSuites = document.getElementById("identicalSuites");
var noSniSuites = document.getElementById("noSniSuites");
if (protocolCount && identicalSuites && noSniSuites) {
    protocolCount = protocolCount.value;
    identicalSuites = identicalSuites.value;
    noSniSuites = noSniSuites.value;
    for (var i = 0; i <= protocolCount; i++) {

        var hideCipher = document.getElementById('hidecipher'+i);
        var showCipher = document.getElementById('showcipher'+i);

        if(hideCipher && showCipher) {
            hideCipher.onclick = function() {
                hide(this.getAttribute("cipher"));
            }

            showCipher.onclick = function() {
                show(this.getAttribute("cipher"));
            }
        }

        // Hide suites if suites exists observed in highest supported protocol suites
        // And always hide no sni suites
        if (protocolCount > 1 && i > 1 && identicalSuites === "true") {
                hide('cipher'+i);
        } else if (noSniSuites == "true" && i == protocolCount) {
                hide('cipher'+i);
        }
    }
}

// Bind onclick to Http block buttons
var hidehttp = document.getElementById('hidehttp');
var showhttp = document.getElementById('showhttp');
if (hidehttp && showhttp) {
    hidehttp.onclick = function() {
        hide("http");
    }

    showhttp.onclick = function() {
        show("http");
    }
}

// Hide http section on initial load
hide('http');

// Bind onclick to simulations section
var hidesimulations = document.getElementById('hidesimulations');
var showsimulations = document.getElementById('showsimulations');
var expandsimulations = document.getElementById('expandsimulations');
if (hidesimulations && showsimulations && expandsimulations) {
        hidesimulations.onclick = function() {
            hide("simulations");
        }
        showsimulations.onclick = function() {
            show("simulations");
        }
        expandsimulations.onclick = function() {
            show("simulations");
        }
}

// Hide not simulated simulations section on initial load
hide('simulations');
var notsimulatedcount = document.getElementById('notSimulatedCount');
if (notsimulatedcount && notsimulatedcount.value < 3) {
    // show not simulated clients if count < 3
    show('simulations');
}

//Multiple Trust store
function openTrustPath(evt, trustPath) {
    // Declare all variables
    var i, tabcontent, tablinks;
    var selectedChain = trustPath[trustPath.length - 1];
    trustPath = trustPath + 'content';
    // Get all elements with class="tabcontent+respective chain number" and hide them
    tabcontent = document.getElementsByClassName("tabcontent"+selectedChain+" fadeEffect");
    for (i = 0; i < tabcontent.length; i++) {
        tabcontent[i].style.display = "none";
    }

    // Get all elements with class="tablinks+respective chain number" and remove the class "active"
    tablinks = document.getElementsByClassName("tablinks"+selectedChain);
    for (i = 0; i < tablinks.length; i++) {
        tablinks[i].className = tablinks[i].className.replace(" active", "");
    }

    // Show the current tab, and add an "active" class to the button that opened the tab
    document.getElementById(trustPath).style.display = "block";
    evt.currentTarget.className += " active";
}

// Bind Multiple TrustStores button
for (var i = 1; i <= chainCount; i++) {
    var tablinks = document.getElementsByClassName("tablinks"+i);
    for (var j = 0; j < tablinks.length; j++) {
        tablinks[j].onclick = function(event) {
            openTrustPath(event, this.id);
        }
    }
}

// Show/Select Mozilla Store for all by default
for (var i = 1; i <= chainCount; i++) {
    document.getElementById("Mozilla"+i).click();
}
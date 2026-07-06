// Elements
const envelope = document.getElementById("envelope");
const startScreen = document.getElementById("startScreen");
const inviteScreen = document.getElementById("inviteScreen");

const popup = document.getElementById("popup");
const rsvpBtn = document.getElementById("rsvpBtn");
const closePopup = document.getElementById("closePopup");
const form = document.getElementById("rsvpForm");

// -----------------------
// Open Envelope
// -----------------------

envelope.addEventListener("click", () => {

    envelope.classList.add("open");

    // Confetti
    setTimeout(() => {

        confetti({
            particleCount: 180,
            spread: 90,
            origin: { y: 0.6 }
        });

    }, 900);

    // Show invitation
    setTimeout(() => {

        startScreen.style.display = "none";
        inviteScreen.style.display = "flex";

    }, 1700);

});

// -----------------------
// Open RSVP
// -----------------------

rsvpBtn.addEventListener("click", () => {

    popup.style.display = "flex";

});

// -----------------------
// Close RSVP
// -----------------------

closePopup.addEventListener("click", () => {

    popup.style.display = "none";

});

// Close if clicking outside popup

popup.addEventListener("click",(e)=>{

    if(e.target===popup){

        popup.style.display="none";

    }

});

// -----------------------
// Submit RSVP
// -----------------------

form.addEventListener("submit", async function(e){

    e.preventDefault();

    const data = {

        name:document.getElementById("name").value,

        guests:document.getElementById("guests").value,

        message:document.getElementById("message").value

    };

    // **************
    // Replace this URL later
    // **************

    const WEBAPP_URL = "https://script.google.com/macros/s/AKfycbyL5X3SBG4VRKGJYjfMWiTa24vm8Bs_OFAdKbjIPoQUhxZNV9fNErnNEMVtbhO_sxqANA/exec";

    try{

        if(WEBAPP_URL.includes("PASTE")){

            alert("RSVP saved locally.\nWe'll connect Google Sheets next!");

            console.log(data);

        }else{

            await fetch(WEBAPP_URL,{

                method:"POST",

                mode:"cors",

                headers:{
                    "Content-Type":"application/json"
                },

                body:JSON.stringify(data)

            });

            alert("Thank you! Your RSVP has been received!");

        }

        form.reset();

        popup.style.display="none";

    }catch(err){

        alert("Something went wrong.");

        console.error(err);

    }

});

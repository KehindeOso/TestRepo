<template>
   <div class="container">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/5.15.3/css/all.min.css">

        <div class="forms_container">
            <div class="signin-signup">
                <form action="" class="sign-in-form" id="sign-in"> 
                    <h2 class="title">Sign in</h2>
          <div class="input-field">
                        <i class = "fas fa-user"></i>
                        <input type="text" placeholder="Username" id = "username">
                    </div>
                    <div class="input-field">
                        <i class = "fas fa-lock"></i>
                        <input type="password" placeholder="Password" id = "password">
                    </div>
                   <input type="submit" value="Sign in" class="btn solid" id="login_btn">
                    <div id="popup">
                        <div class="content">
                            <h2>welcome back, Madison!</h2>
                            <h4>start typing for evexia can notice you!</h4>
                            <router-link to = "/userprofile"><div class="inputBox">
                                <input type="submit" value="next" class="btn">
                            </div></router-link>
                        </div>
                        <a class="close">
                            <img src="@/assets/cancel.png" style="width:1em; height:1em;" onclick="popupToggle();">
                        </a>
                    </div>
                    <p class="social-text">Or sign in with: </p>
                    <div class="social-media">
                        <router-link to ="/facebook"><a href="#" class="social-icon">
                            <i class="fab fa-facebook-f"></i>
                        </a></router-link>
                        <a href="#" class="social-icon">
                            <i class="fab fa-twitter"></i>
                        </a>
                        <a href="#" class="social-icon">
                            <i class="fab fa-google"></i>
                        </a>
                        <a href="#" class="social-icon">
                            <i class="fab fa-linkedin-in"></i>
                        </a>
                    </div>
                </form>

                <form action="" class="sign-up-form"> 
                    <h2 class="title">Sign Up!</h2>
                    <div class="input-field">
                        <i class = "fas fa-user"></i>
                        <input type="text" placeholder="Username">
                    </div>
                    <div class="input-field">
                        <i class = "fas fa-envelope"></i>
                        <input type="text" placeholder="Email">
                    </div>
                    <div class="input-field">
                        <i class = "fas fa-lock"></i>
                        <input type="password" placeholder="Password">
                    </div>
                    <input type="submit" value="Sign up" class="btn solid">
                    <p class="social-text">Or sign up with: </p>
                    <div class="social-media">
                        <a href="#" class="social-icon">
                            <i class="fab fa-facebook-f"></i>
                        </a>
                        <a href="#" class="social-icon">
                            <i class="fab fa-twitter"></i>
                        </a>
                        <a href="#" class="social-icon">
                            <i class="fab fa-google"></i>
                        </a>
                        <a href="#" class="social-icon">
                            <i class="fab fa-linkedin-in"></i>
                        </a>
                    </div>
                </form>
            </div>
        </div>
   <div class="panels-container">
       <div class="panel left-panel">
           <div class="content">
               <h3>New here?</h3>
               <p>Evexia is a mental health suggestor that helps users feel better in seeking mental health resources.</p>
               <button class="btn transparent" id="sign-up-btn">Sign up</button>
           </div>
           <img src="@/assets/IMG_1625-removebg-preview.png" class="image" alt="Evexia logo">
       </div>

       <div class="panel right-panel">
        <div class="content">
            <h3>Already have an account?</h3>
            <p>Evexia is a mental health suggestor that helps users feel better in seeking mental health resources.</p>
            <button class="btn transparent" id="sign-in-btn">Sign in</button>
        </div>
        <img src="@/assets/IMG_1625-removebg-preview.png" class="image" alt="Evexia logo">
    </div>
   </div>
   </div>
</template>

<script>

// (A) DATA OBJECT
var user = {
    name : "Madison",
    email : "jane123@gmail.com",
    password: "PassWord1!"
  };
   
  // (B) STORE IN LOCAL STORAGE
  // Note: JSON encode
  localStorage.setItem("User", JSON.stringify(user));
   
  // (C) RETRIEVE
  // Note: JSON decode
  user = localStorage.getItem("User");
  user = JSON.parse(user);
  console.log(user);

window.addEventListener('click', function (){

    const sign_in_btn = document.querySelector("#sign-in-btn");
    const sign_up_btn = document.querySelector("#sign-up-btn");
    const container = document.querySelector(".container");
    const popup = document.getElementById('popup');
    const login = document.querySelector('#login_btn');
    const formlog = document.getElementById("sign-in");
    
    sign_up_btn.addEventListener('click', () => {
        container.classList.add("sign-up-mode");
    });

    sign_in_btn.addEventListener('click', () => {
        container.classList.remove("sign-up-mode");
    });

    function popupToggle(){
        popup.classList.toggle('active');
    }

   
    login.addEventListener('click', (e) => {
        e.preventDefault();
        const username = formlog.username.value;
        const password = formlog.password.value;
        if(username === "Madison" && password === "PassWord1!"){
            popupToggle();
        }
        else{
            alert("This seems like you have inputted the wrong information. Please try again!")
        }
    });
})
</script>

<style lang="scss" scoped>
@import url("https://fonts.googleapis.com/css2?family=Nunito+Sans:wght@400;600;700;800&display=swap");

*{
    padding: 0;
    margin: 0;
    box-sizing: border-box;
}

body, input{
    font-family: 'Nunito Sans', sans-serif;
}

.container{
    position: relative;
    width: 100%;
    min-height: 100vh;
    background-color: #fff;
    overflow: hidden;
}
.container::before{
    content: '';
    position: absolute;
    width: 2000px;
    height: 2000px;
    border-radius: 50%;
    background: linear-gradient(-45deg, rgb(171, 147, 255), rgb(255, 255, 255));
    top: -10%;
    right: 48%;
    transform: translateY(-50%);
    z-index: 6;
    transition: 1.8s ease-in-out;
}

.forms-container{
    position: absolute;
    width: 100%;
    height: 100%;
    top: 0;
    left: 0;

}

.signin-signup{
    position: absolute;
    top: 50%;
    left: 75%;
    transform: translate(-50%, -50%);
    width: 50%;
    display: grid;
    grid-template-columns: 1fr;
    z-index: 5;
    transition: 1s 0.7s ease-in-out;
}

form.sign-in-form{
    z-index: 2;
}

form.sign-up-form{
    z-index: 1;
    opacity: 0;
}

form{
    display: flex;
    align-items: center;
    justify-content: center;
    flex-direction: column;
    padding: 0 5rem;
    overflow: hidden;
    grid-column: 1 / 2;
    grid-row: 1 / 2;
    transition: 0.2s 0.7s ease-in-out;
}

.title{

    font-size: 2.2rem;
    color: black;
    margin-bottom: 10px;
}

.input-field {
    max-width: 300px;
    width: 100%;
    height: 55px;
    background-color: rgb(166, 131, 248) ;
    margin: 10px 0;
    border-radius: 55px;
    display: grid;
    grid-template-columns: 15% 85%;
    padding: 0 .4rem;
}

.input-field i{
    text-align: center;
    line-height: 55px;
    color: aquamarine;
    font-size: 1.1rem;
}

.input-field input{
    background: none;
    outline: none;
    border: none;
    line-height: 1;
    font-weight: 600;
    font-size: 1.1rem;
    color: white;
}

.input-field input::placeholder{
    color:rgb(99, 98, 98);
    font-weight: 500;
}

.btn{
    width: 150px;
    height: 49px;
    border: none;
    outline: none;
    border-radius: 49px;
    cursor: pointer;
    background-color: rgb(203, 121, 241);
    font-weight: 600;
    margin: 10px 0;
    transition: .5s;
}

.btn:hover{
    background-color: rgb(203, 162, 250);
    letter-spacing: 4px;
}

.social-text{
    padding: .7rem 0;
    font-size: 1rem;
    color: black;
}


.social-media{
    display: flex;
    justify-content: center;
}

.social-icon{
    height: 46px;
    width: 46px;
    border: 1px solid black;
    margin: 0 0.45rem;
    display: flex;
    justify-content: center;
    align-items: center;
    text-decoration: none;
    color: purple;
    font-size: 1.1rem;
    border-radius: 50%;
    transition: .3s;
}

.social-icon:hover{
    color:rgb(166, 131, 248);
    border-color: rgb(167, 255, 182);

}

.panels-container{
    position: absolute;
    width: 100%;
    height: 100%;
    top: 0;
    left: 0;
    display: grid;
    grid-template-columns: repeat(2, 1fr);
    color: black;
}

.panel{
    display: flex;
    flex-direction: column;
    align-items: flex-end;
    justify-content: space-around;
    text-align: center;
    z-index: 7;
}

.left-panel{
    pointer-events: all;
    padding: 3rem 17% 2rem 12%;
}

.right-panel{
    pointer-events: none;
    padding: 3rem 12% 2rem 17%;
}

.panel .content{
    color: #fff;
    transition: .9s .6s ease-in-out;
    
}

.panel h3{
    font-weight: 600;
    line-height: 1;
    font-size: 1.5rem;
}

.panel p {
    font-size: 0.95rem;
    padding: 0.7rem 0;
    color: white;
   
}

.btn.transparent{
    margin: 0;
    background: none;
    border: 2px solid #fff;
    width: 130px;
    height: 41px;
    font-weight: 600;
    font-size: 0.8rem;

}

.image{
    width: 100%;
    transition: 1.1s .4s ease-in-out;
}

.right-panel .content, .right-panel .image{
    transform: translateX(800px);
}

/* animation times */

.container.sign-up-mode:before{
    transform: translate(100%, -50%);
    right: 52%;
}

.container.sign-up-mode .left-panel .image,
.container.sign-up-mode .left-panel .content{
    transform: translateX(-800px);
}

.container.sign-up-mode .right-panel .content, 
.container.sign-up-mode .right-panel .image {
    transform: translateX(0px);
}

.container.sign-up-mode .left-panel{
    pointer-events: none;
}

.container.sign-up-mode .right-panel{
    pointer-events: all;
}

.container.sign-up-mode .signin-signup{
    left: 25%;
}

.container.sign-up-mode form.sign-in-form{
    z-index: 1;
    opacity: 0;
}

.container.sign-up-mode form.sign-up-form{
    z-index: 2;
    opacity: 1;
}

#popup{
    position: fixed;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    z-index: 1000;
    background: #fff;
    width: 450px;
    padding: 50px 50px 50px;
    box-shadow: 0 15px 30px rgba(0, 0, 0, .08);
    transition: 1s;
    visibility: hidden;
}

#popup.active{
    visibility: visible;
    top: 50%
}

#popup .content{
    position: relative;
    width: 100%;
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: column;
}

#popup .content h2{
    font-size: 27px;
    font-weight: 700;
    color: rgb(165, 85, 240);
    margin: 20px 0 10px;

}

#popup .content h4{
    font-size: 17px;
    color:rgb(162, 168, 173);
}

#popup .content .inputBox{
    position: relative;
    width: 100%;
    margin-top: 20px;
    display: flex;
    justify-content: center;
    align-items: center; 
    
}

#popup .content .inputBox input{
    width: 60vh;
    border: 1px solid blueviolet;
    border-radius: 15px;
    padding: 15px;
    outline: none;
    font-size: 18px;
    font-weight: 700;
    box-shadow: 0 1px 2px rgba(0, 0, 0, .02);
}

#popup .content .inputBox input[type="submit"]{
    background: rgb(165, 85, 240);
    color: #fff;
    border: none;

}

.close{

    position: absolute;
    top: 20px;
    left: 20px;
    cursor: pointer;
}


@media(max-width:870px){
    .container{
        min-height: 800px;
        height: 100vh;
    }

    .container:before{
        width: 1500px;
        height: 1500px;
        left: 30%;
        bottom: 68%;
        transform: translateX(-50%);
        right: initial;
        top: initial;
        transition: 2s ease-in-out;
    }

    .signin-signup{
        width: 100%;
        left: 50%;
        top: 95%;
        transform: translate(-50%, -100%);
        transition: 1s .8s ease-in-out;
    }

    .panels-container{
        
        z-index: 10;
        grid-template-columns: 1fr;
        grid-template-rows: 1fr 2fr 1fr;
        color: black;
    }

    .panel{
        flex-direction: row;
        justify-content: space-around;
        align-items: center;
        padding: 2.5rem 8%;
    }

    .panel .content{
        padding-right: 15%;
        transition: .9s .8s ease-in-out;

    }

    .panel h3{
        font-size: 1.2rem;
        padding: 0.5rem 0;
        color: black;
    }

    .btn.transparent{
        width: 110px;
        height: 35px;
        font-size: 0.7rem;
    }

    .image{
        width: 200px;
        transition: .9s .6s ease-in-out;
    }

    .left-panel{
        grid-row: 1 / 2;
    }

    .right-panel{
        grid-row: 3 / 4;
    }

    .right-panel .content, .right-panel .image{
        transform: translateY(300px);

    }
    
    .container.container.sign-up-mode:before{
        transform: translate(-50%, 100%);
        bottom: 32%;
        right: initial;
    }

    .container.container.sign-up-mode .left-panel .image,
    .container.container.sign-up-mode .left-panel .content{
        transform: translateY(-300px);

    }

    .container.sign-up-mode .signin-signup{
        top: 5%;
        transform: translate(-50%, 0);  
        left: 50%
    }
}

@media(max-width: 570px){
    form{
        padding: 0 1.5rem;
    }

    .image{
        display: none;
    }

    .panel .content{
        padding: 0.5rem 1rem;
    }

    .container:before{
        bottom: 72%;
        left: 50%;
    }

    .container.container.sign-up-mode:before{
        bottom: 28%;
        left: 50%;
    }
}
</style>
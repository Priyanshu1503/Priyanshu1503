<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/5.15.4/css/all.min.css">
  <title>Document</title>
  <style>
    *{
      margin: 0;
      padding: 0;
      box-sizing: border-box;
      font-family: sans-serif;
      text-transform: uppercase;
      text-decoration: none;
    }
    body{
      min-height: 100vh;
      background-color: rgb(212, 218, 215);
      background-size: cover;
      background-position: center;
    }
    header{
      position: absolute;
      top: 0;
      left: 0;
      right: 0;
      background: #f3f1f1;
      box-shadow: 0 5px 10px rgba(0,0,0,0.1);
      padding: 10px 7%;
      display: flex;
      align-items: center;
      justify-content: space-between;
      z-index: 1000;
    }
    header .logo{
      font-weight: bolder;
      font-size: 25px;
      color: #333;
    }
    header .navbar ul{
      list-style: none;
    }
    header .navbar ul li{
      position: relative;
      float: left;
    }
    header .navbar ul li a{
      font-size: 20px;
      padding: 20px;
      color: #333;
      display: block;
    }
    header .navbar ul li a:hover{
      background: #333;
      color: #fff;
    }
    header .navbar ul li ul{
      position: absolute;
      left: 0;
      width: 200px;
      background: #fff;
      display: none;
    }
    header .navbar ul li ul li{
      width: 100%;
      border-top: 1px solid rgba(0,0,0,0.1);
    }
    header .navbar ul li ul li ul{
      left: 200px;
      top: 0;
    }
    header .navbar ul li:focus-within >ul,
    header .navbar ul li:hover >ul{
      display: initial;
    }
    #menu-bar{
      display: none;
    }
    header label{
      font-size: 20px;
      color: #333;
      cursor: pointer;
      display: none;
    }
    @media (max-width:991px){
      header{
        padding: 20px;
      }
      header label{
        display: initial;
      }
      header .navbar{
        position: absolute;
        top: 100%;
        left: 0;
        right: 0;
        background: #fff;
        border-top: 1px solid rgba(0,0,0,0.1);
        display: none;
      }
      header .navbar ul li{
        width: 100%;
      }
      header .navbar ul li ul{
        position: relative;
        width: 100%;
      }
      header .navbar ul li ul li{
        background: #eee;
      }
      header .navbar ul li ul li ul{
        width: 100%;
        left: 0;
      }
      #menu-bar:checked ~.navbar{
        display: initial;
      }
    }
    .heading{
      margin-top: 10%;
      font-size: 40px;
      text-align: center;
      color: #000000;
      margin-bottom: 40px;
    }
    .table{
      margin-left: 10%;
      width: 80%;
      border-collapse: collapse;
    }
    .table thead{
      background-color: #200049;
    }
    .table thead tr th{
      font-size: 14px;
      font-weight: 500;
      letter-spacing: 0.35px;
      color: #fff;
      opacity: 1;
      padding: 12px;
      vertical-align: top;
      border: 1px solid #dee2e685;
    }
    .table tbody tr td{
      font-size: 14px;
      letter-spacing: 0.35px;
      font-weight: 700;
      color: #000000;
      background-color: #aaafb6a2;
      padding: 8px;
      text-align: center;
      border: 1px solid #dee2e685;
    }
    .table .text_open{
      font-size: 14px;
      font-weight: bold;
      letter-spacing: 0.35px;
      color: rgb(23, 221, 16);
    }
    .table tbody tr td .btn{
      width: 130px;
      text-decoration: none;
      line-height: 35px;
      display: inline-block;
      background-color: #ff1046;
      font-weight: 500;
      color: #fff;
      text-align: center;
      vertical-align: middle;
      user-select: none;
      border: 1px solid transparent;
      font-size: 14px;
      opacity: 1;
    }
    @media (max-width:991px){
      .heading{
        margin-top: 20%;
      }
      .table thead{
        display: none;
      }
      .table, .table tbody, .table tr, .table td{
        display: block;
        width: 95%;
      }
      .table tr{
        margin-bottom: 15px;
      }
      .table tbody tr td{
        text-align: right;
        padding-left: 50%;
        position: relative;
      }
      .table td::before{
        content: attr(data-label);
        position: absolute;
        left: 0;
        padding-left: 15px;
        font-weight: 600;
        font-size: 14px;
        text-align: left;
      }
    }


    .popup-screen{
  z-index: 999999;
  position: fixed;
  background: rgba(255, 255, 255, 0.1);
  backdrop-filter: blur(20px);
  width: 100%;
  height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  visibility: hidden;
  transition: 0.5s ease;
  transition-property: visibility;
}

.popup-screen.active{
  visibility: visible;
}

.popup-box{
  position: relative;
  background: rgba(255, 255, 255, 0.8);
  backdrop-filter: blur(10px);
  width: 350px;
  height: 200px;
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  margin: 20px;
  padding: 50px 40px;
  border-radius: 20px;
  box-shadow: 0 5px 25px rgb(0 0 0 / 20%);
  transform: scale(0);
  transition: 0.5s ease;
  transition-property: transform;
}

.popup-screen.active .popup-box{
  transform: scale(1);
}

.popup-box .text{
  margin-left: 5%;
  margin-top: 3%;
  justify-content: center;
  text-align: center;
}
.popup-box .text h2 i{
  font-size: 40px;
  padding: 10px 15px;
}
.popup-box .text h2 a{
  padding: 3px 5px;
  background-color: #000;
  border-radius: 20px;
  color: #009879;
}
.popup-box .text h2{
  line-height: 90px;
  
}

.close-btn{
  position: absolute;
  font-size: 1em;
  top: 0;
  right: 0;
  margin: 15px;
  cursor: pointer;
  opacity: 0.5;
  transition: 0.3s ease;
  transition-property: opacity;
}

.close-btn:hover{
  opacity: 1;
}



@media (max-width: 990px){
  section{
    padding: 50px 30px;
  }

  .home{
    display: block;
  }

  .image{
    width: 100%;
  }

  .info{
    width: 100%;
    margin-top: 15px;
  }
}


.footer{
  width:100%;
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding:1rem 2rem;
  margin-top: 20%;
  background-color: #009879;
}

.footer h1{
  color:#fff;
  letter-spacing: .1rem;
  font-weight: 400;
}

.footer .icons a{
  color:#fff;
  font-size: 1.8rem;
  padding:0 1rem;
}
  </style>
</head>
<body>
  <header>
    <a href="#" class="logo">LOGO</a>
    <input type="checkbox" id="menu-bar">
    <label for="menu-bar">Menu</label>

    <nav class="navbar">
      <ul>
        <li><a href="#">HOME</a></li>
        <li><a href="#">ABOUT</a></li>
        <li><a href="#">CERTIFICATE +</a>
          <ul>
            <li><a href="#">MARKETING</a></li>
            <li><a href="#">IT</a></li>
            <li><a href="#">FINANCE</a></li>
          </ul>
        </li>
        <li><a href="#">INTERNSHIP</a></li>
        <li><a href="#">JOBS +</a>
          <ul>
            <li><a href="#">TECHNICAL +</a>
              <ul>
                <li><a href="#">FRESHER</a></li>
                <li><a href="#">EXPERIENCE</a></li>
              </ul>
            </li>
            <li><a href="#">NON-TECHNICAL +</a>
              <ul>
                <li><a href="#">FRESHER</a></li>
                <li><a href="#">EXPERIENCE</a></li>
              </ul>
            </li>
          </ul>
        </li>
        <li><a href="#">CONTACT US</a></li>
      </ul>
    </nav>
  </header>

  <div class="popup-screen">
    <div class="popup-box">
      <i class="fas fa-times close-btn"></i>
      <div class="text">
        <h2><i class="fab fa-whatsapp-square"></i><a href="#">WHATSAPP</a></h2>
        <hr width="250">
        <h2><i class="fab fa-telegram"></i><a href="#">TELEGRAM</a></h2>
      </div>
    </div>
  </div>


  <div class="table-con">
    <h1 class="heading">JOB DRIVE</h1>
    <table class="table">
      <thead>
        <tr>
          <th>COMPANY NAME</th>
          <th>JOB TYPE</th>
          <th>LOCATION</th>
          <th>ACCESSIBLE</th>
          <th>#</th>
        </tr>
      </thead>
      <tbody>
        <tr>
        <td data-label="COMPANY NAME">RELIANCE</td>
        <td data-label="JOB TYPE">FULL TIME</td>
        <td data-label="LOCATION">INDORE</td>
        <td data-label="ACCESSIBLE"><span class="text_open">[available]</span></td>
        <td data-label="#"><a href="page.html" class="btn">Apply Now</a></td>
      </tr>
      <tr>
        <td data-label="COMPANY NAME">WIPRO</td>
        <td data-label="JOB TYPE">FULL TIME</td>
        <td data-label="LOCATION">BANGALORE</td>
        <td data-label="ACCESSIBLE"><span class="text_open">[available]</span></td>
        <td data-label="#"><a href="#" class="btn">Apply Now</a></td>
      </tr>
      <tr>
        <td data-label="COMPANY NAME">FACEBOOK</td>
        <td data-label="JOB TYPE">FULL TIME</td>
        <td data-label="LOCATION">MUMBAI</td>
        <td data-label="ACCESSIBLE"><span class="text_open">[available]</span></td>
        <td data-label="#"><a href="#" class="btn">Apply Now</a></td>
      </tr>
      <tr>
        <td data-label="COMPANY NAME">GOOGLE</td>
        <td data-label="JOB TYPE">FULL TIME</td>
        <td data-label="LOCATION">DELHI</td>
        <td data-label="ACCESSIBLE"><span class="text_open">[available]</span></td>
        <td data-label="#"><a href="#" class="btn">Apply Now</a></td>
      </tr>
      </tbody>
    </table>
  </div>

  <section class="footer">



    <div class="icons">
      <a href="#" class="fab fa-facebook-f"></a>
      <a href="#" class="fab fa-twitter"></a>
      <a href="#" class="fab fa-instagram"></a>
    </div>
    
    </section>

  <script type="text/javascript">
    const popupScreen = document.querySelector(".popup-screen");
    const popupBox = document.querySelector(".popup-box");
    const closeBtn = document.querySelector(".close-btn");

    window.addEventListener("load", () => {
      setTimeout(() => {
        popupScreen.classList.add("active");
      }, 1000); //Popup the screen in 02 seconds after the page is loaded.
    });

    closeBtn.addEventListener("click", () => {
      popupScreen.classList.remove("active"); //Close the popup screen on click the close button.
    });
    </script>
</body>
</html>
